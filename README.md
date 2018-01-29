# Unnamed GUI Asset (matharoo)
## Documentation

Creating & managing UI elements is easier than ever!

## [Jump To GIFs](https://github.com/gurpreetsinghmatharoo/ui-asset-documentation/blob/master/README.md#gifs)

# Note

Arguments inside [] are optional

# Elements
# Buttons

Use button_create() to create a button.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**text:** text to display

**[animate]:** whether to enable effects on the button (*default: true*)

Store the returned id in a variable.

### Example
```buttonBuy = button_create(32, 32, 64, 16, "Buy Now!");```
                   
## button_clicked()

button_clicked(id) checks whether the button was clicked in this step.

### Example
```if (button_clicked(buttonBuy)) buyItem();```

## button_script()

Using button_script(id, script) you can assign a script to run each the button is 
clicked. It will automatically run whenever the button is pressed.

### Example
```button_script(buttonBuy, buyItem);```
        
## Button position

You can use a button's x/y variables to move it.

### Example
```buttonBuy.x = 256;```
        
```buttonBuy.y += 4;```

# Panels

Panels are rectangular areas that group buttons inside them.

Use panel_create() to create a panel.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

[text]: text to display
        
Store the returned id in a variable.

### Example
```panelMain = panel_create(8, 8, 256, 128, "Main");```
        
## Adding elements inside a panel

Use panel_add(panel, ids) to add UI elements inside a panel.

Those elements will now move with the panel whenever it is moved.

### Example
```panel_add(panelMain, buttonBuy, buttonCancel);```
        
You can add up to 15 elements at once.

## Panel position

Use panel_pos(panel, x, y) to change a panel's position.

Use panel_move(panel, x+, y+) to add to the position of a panel.

# Text Fields

Use textbox_create() to create a textbox.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**[text]:** text to display, optional

## Text

Use the `eText` variable to get the text currently in a text field.

### Example
```
var tf_text = tfName.eText; //Gets the text inside the 'tfName' text field
```

# Sliders

Use slider_create() to create a slider.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**[head_pos]:** initial position of the head, optional, 0-1

**[text]:** text to display, optional

**head_pos** is where position of the head on the slider, and it ranges from 0 to 1.

## Head Position

Use the `headPos` variable to get the head position of a slider.
It will be in a 0 to 1 range.

### Example
```
var amount = sdAmount.headPos; //Gets the head position of the 'sdAmount' slider
```

# GUI Mode

Use `ui_gui_mode(true/false)` to enable/disable GUI mode.

*Default: true*

With GUI mode on, the UI will be drawn on the screen/GUI layer.
Without GUI mode, it will be drawn inside the room.

# Manual Placement

If you don't want to use code and want to manually place the UI elements
in the room, you can do so. But, you will need to fill in some variables
in those instances' Creation Codes.

For that particular element, open its create script (for example, 'button_create'
for buttons) and go to the '//Set variables' part. See which variables
are being set, and initialize them in the Creation Code.

Of course, you don't need to do this if you *are* using the scripts.

Also, the elements you place using the room editor are not drawn to
the GUI layer.

# Destroying

Use `instance_destroy(id)` to destroy UI elements you create.

# Sprites

Use `ui_sprite()` to change the sprites for every type of element.

### Arguments:
**Buttons:** Sprite for buttons

**Panels:** Sprite for panels

**Text Field:** Sprite for text fields

**Slider:** Sprite for sliders

The sprite must a square sprite of a 3x3 grid. It'll be [9-slice-stretched](https://marketplace.yoyogames.com/assets/6397/draw-9-slice-sprites) to fit the GUI.

If you don't want to change the sprite for any of these arguments, just pass -1.

# GIFs

## Panel with three buttons

![Panels](https://i.imgur.com/nN8HgNw.gif)

## Text Field

![Text Field](https://i.imgur.com/xHJy4sX.gif)
