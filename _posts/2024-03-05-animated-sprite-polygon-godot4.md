---
layout: post
title: Godot - making polygon colliders from AnimatedSprite2D
date: 2024-03-05
#description: an example of a blog post with table of contents
tags: code
related_posts: false
# toc:
#   beginning: true

---

<div class="row mt-3">
     <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/poly_animsprite_fox1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
     <div class="col-2 mt-3 mt-md-0"></div>
</div>

I made a little tool script that can generate polygon shapes for Area2D nodes for each frame of an AnimatedSprite2D, and make those areas active and inactive at runtime. It is based on a few assumptions, like your AnimatedSprite2D doesn't use offsets and your AtlasTextures don't use margins, but I'm sure those would be easy to add in if needed.

The road to it was a bit bumpy, though. It has been a while since I made it so I don't rememeber all the details but I still want to share my journey, as well as the tool's code.

### Context

In January I took some time off to learn a bit more about multiplayer games in Godot by making a fighting game (er, following a tutorial that is). Fighting games are pretty complex so a tutorial could be a good primer, and I already made some action games before so that knowledge could translate here too.

I like Super Smash Bros so I was very inclined to follow <a href="https://www.youtube.com/watch?v=FKMBkZsPCCA&list=PLeJDGeZe3by2tQIJmCZfaSRl95cot070t">this tutorial series by Apano</a>. There are a few design patterns I don't totally agree with but it's very serviceable. I promptly implemented everything and had fun with how smooth it felt. Just one problem: the tutorial used the character's solid collision square box as the damage hurtbox, which meant it couldn't quite reflect the different sprites. It also meant, for the game to be juicy, you had to exaggerate the attack hitboxes which would further highlight the problem.

<div class="row mt-3">
     <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/poly_animsprite_fox2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
     <div class="col-2 mt-3 mt-md-0"></div>
</div>

Side note: I didn't have a second controller to test multiplayer, but I've since learned Godot can recognize virtual controllers from _Parsec_. It has been my favorite way to test multiplayer games. I'm not being paid to say this (unfortunately) but it's pretty cool.

### Research

TheShaggyDev is one of my favorite Godot creators as he dives deep into his design process for code and project structure, and many of his projects align with my likes. I was delighted to know he had made a video on getting polygon shapes (for static colliders) from Sprite2D nodes.
<div class="embed-responsive embed-responsive-16by9">
    {% include video.html path="https://www.youtube.com/embed/Btk8IzhvaDo?si=YIluHglNY37pbH3S" class="img-fluid rounded  z-depth-1" %}
</div>
<div class="caption">There's also a text version linked in the video's description.</div>

That's cool and all, but how would I do that for every frame in an AnimatedSprite2D? I couldn't generate the polygons at runtime as the algorithm is pretty slow, so I would need to generate one shape for each frame, then activate and deactivate them at runtime. I needed to make a tool script that would generate all my polygons when I ticked a checkbox (in the lack of tool script buttons).

```gdscript
func run_tool():
	var anim_sprite := get_parent() as AnimatedSprite2D
	if not anim_sprite:
		push_error("Parent is not AnimatedSprite2D")
        return

	hurtbox_dict = {}
	
	var bitmap : BitMap
	var current_texture : Texture2D
	
	var old_hurtboxes = get_parent().get_parent().get_node_or_null("Hurtboxes")
	if old_hurtboxes:
		old_hurtboxes.queue_free()
	
	var results_node := Node2D.new()
	anim_sprite.add_child(results_node)
	results_node.owner = get_tree().edited_scene_root
	results_node.name = "Hurtboxes"
	hurtboxes_path = get_path_to(results_node)
```

Now I just had to find the sprite's texture as it was shown on the AnimatedSprite2D, and make polygons from that. How hard could it be? It's probably right there in the documentation, right?

### Getting the frame's texture.

Most of my frames were imported as AtlasTextures for brevity's sake and to not bloat each character's folder with a hundred files; if I had each frame separately I could probably used ShaggyDev's aproach by using a simple Sprite2D and changing its frame to another file for each shape. Following that approach approach of getting the texture directly wouldn't work with AnimatedSprite2D as there was no one single texture for the entire animation; each frame of each animation can have a texture taken from a separate file, or an atlas made from a file, or even a blank texture.

For a long time I tried creating a new _viewport_, rendering the AnimatedSprite2D there, saving the _render texture_ and using that, but in retrospect even if it worked, it wouldn't have accounted for different sizes in sprite frames... I wish I had commited every single attempt just to look back on them, because I had some really absurd ideas. I'm not even sure if it every rendered anything, although I remember getting a polygon from an entirely unrelated section of the Atlas.

<i>Eventually, I found: Texture2D SpriteFrames.get_frame_texture(anim: StringName, idx: int). It's in the documentation.</i>

So that was a relief. I just needed to make an image from it... wait, why is it blank?
For whatever reason (and without breakpoints for tool scripts it took a whole morning to find out) the generated texture when converted to a bitmap wouldn't show as a cut-up region of its AtlasTexture during the tool's execution. It was entirely blank. I tied to print the "region" field but it was all 0,0. I couldn't figure out why for another long period of time.

```gdscript
var sprite_frames : SpriteFrames = anim_sprite.sprite_frames
for animation_name in sprite_frames.get_animation_names():
    anim_sprite.animation = animation_name
    
    for frame_index in range(sprite_frames.get_frame_count(animation_name)):
        anim_sprite.frame = frame_index
        
        bitmap = BitMap.new()
        current_texture = sprite_frames.get_frame_texture(animation_name, frame_index)
```

My final solution was to get the atlas and make it into an image, as before. I finally found the AtlasTexture "region" field which this time had actual values in it. Then, the fruit of another half an hour of reading documentation I found code Image.get_region(Rect2Di region) and the region field in the atlas texture worked. Wheww. There's also a tweak for if the source is an entire file or blank.

```gdscript
# inside the inner for loop
if current_texture is AtlasTexture:
    var img = current_texture.atlas.get_image().get_region(current_texture.region)
    bitmap.create_from_image_alpha(img)
else: # file or blank
    bitmap.create_from_image_alpha(current_texture.get_image())
```

### Finishing the tool

Now I just needed to generate the polygons. At first I wanted just one Area2D and one polygon per frame, but if the sprite had separate sections that wouldn't add into a single shape they would be skipped. Instead, I have an Area2D for each frame, which can hold multiple polygons if needed. I'm also adding all the node references for each area into a dictionary to avoid excessive get_node calls.

```gdscript
# inside the inner for loop as well
var polys = bitmap.opaque_to_polygons(Rect2i(Vector2(0,0), bitmap.get_size()), epsilon)

var area = Area2D.new()
results_node.add_child(area)
area.owner = get_tree().edited_scene_root
area.name = "%s_%d" % [animation_name, frame_index]
hurtbox_dict[area.name] = get_path_to(area)

for poly in polys:
    var collision_polygon = CollisionPolygon2D.new()
    collision_polygon.polygon = poly
    collision_polygon.position = -bitmap.get_size()/2 # assume centered
    collision_polygon.disabled = true
    collision_polygon.visible = false
    area.add_child(collision_polygon)
    collision_polygon.owner = get_tree().edited_scene_root
```

<div class="row mt-3">
     <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/poly_animsprite_fox1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
     <div class="col-2 mt-3 mt-md-0"></div>
</div>
<div class="caption">Each area has a name matching an animation and a frame index.</div>

### Updating during runtime

The helper node also has functions to be executed at runtime. Currently it waits for signals from the AnimatedSprite2D node, but I'm not sure if it introduces a physics frame of delay or not. Alternatively you could run update_shape inside _physics_process.

```gdscript
func update_shape():
	if not hurtboxes_node: return
    # disable everything
	for inactive_hurtbox : Area2D in hurtboxes_node.get_children():
		disable_area(inactive_hurtbox)
    # enable the active one searching the dict
	var active_hurtbox = get_node(hurtbox_dict["%s_%d" % [current_animation, current_frame]])
	for col in active_hurtbox.get_children():
		col.disabled = false
		col.visible = true
	active_hurtbox.scale = Vector2(
			-1 if animated_sprite.flip_h else 1, 
			-1 if animated_sprite.flip_v else 1)
```

### Code

Here's the entire code for this tool. It is a Node2D that should be inserted as a child of the AnimatedSprite2D to animate, and it will handle changing the hurtboxes at runtime too.

```gdscript
@tool
extends Node2D
## poly_animsprite_helper.gd


@export var epsilon : float = 1.0

@export var generate : bool = false :
	set(value):
		if Engine.is_editor_hint(): run_tool()
		generate = value

@export var hurtbox_dict : Dictionary = {}
@export var hurtboxes_path : NodePath

var current_animation : String = ""
var current_frame : int = 0
var animated_sprite : AnimatedSprite2D
var hurtboxes_node : Node2D


func _ready():
	if not Engine.is_editor_hint():
		animated_sprite = get_parent()
		animated_sprite.animation_changed.connect(_on_animation_changed)
		animated_sprite.frame_changed.connect(_on_frame_changed)
		hurtboxes_node = get_node(hurtboxes_path)


func _on_animation_changed():
	current_animation = animated_sprite.animation
	current_frame = 0
	update_shape()


func _on_frame_changed():
	current_frame = animated_sprite.frame
	update_shape()


func update_shape():
	if not hurtboxes_node: return
	for inactive_hurtbox : Area2D in hurtboxes_node.get_children():
		disable_area(inactive_hurtbox)
	
	var active_hurtbox = get_node(hurtbox_dict["%s_%d" % [current_animation, current_frame]])
	for col in active_hurtbox.get_children():
		col.disabled = false
		col.visible = true
	active_hurtbox.scale = Vector2(
			-1 if animated_sprite.flip_h else 1, 
			-1 if animated_sprite.flip_v else 1)


func disable_area(area:Area2D) -> void:
	for col in area.get_children():
		col.disabled = true
		col.visible = false


func run_tool():
	var anim_sprite := get_parent() as AnimatedSprite2D
	if not anim_sprite:
		push_error("Parent is not AnimatedSprite2D")
		return
	
	hurtbox_dict = {}
	
	var bitmap : BitMap
	var current_texture : Texture2D
	
	var old_hurtboxes = get_parent().get_parent().get_node_or_null("Hurtboxes")
	if old_hurtboxes:
		old_hurtboxes.queue_free()
	
	var results_node := Node2D.new()
	anim_sprite.add_child(results_node)
	results_node.owner = get_tree().edited_scene_root
	results_node.name = "Hurtboxes"
	hurtboxes_path = get_path_to(results_node)
	
	var sprite_frames : SpriteFrames = anim_sprite.sprite_frames
	for animation_name in sprite_frames.get_animation_names():
		anim_sprite.animation = animation_name
		
		for frame_index in range(sprite_frames.get_frame_count(animation_name)):
			anim_sprite.frame = frame_index
			
			bitmap = BitMap.new()
			current_texture = sprite_frames.get_frame_texture(animation_name, frame_index)
			
			if current_texture is AtlasTexture:
				var img = current_texture.atlas.get_image().get_region(current_texture.region)
				bitmap.create_from_image_alpha(img)
			else:
				bitmap.create_from_image_alpha(current_texture.get_image())
			
			
			var polys = bitmap.opaque_to_polygons(Rect2i(Vector2(0,0), bitmap.get_size()), epsilon)
			print(animation_name, "_", frame_index, " ", polys)
			
			var area = Area2D.new()
			results_node.add_child(area)
			area.owner = get_tree().edited_scene_root
			area.name = "%s_%d" % [animation_name, frame_index]
			hurtbox_dict[area.name] = get_path_to(area)
			
			for poly in polys:
				var collision_polygon = CollisionPolygon2D.new()
				collision_polygon.polygon = poly
				collision_polygon.position = -bitmap.get_size()/2
				collision_polygon.disabled = true
				collision_polygon.visible = false
				area.add_child(collision_polygon)
				collision_polygon.owner = get_tree().edited_scene_root
```