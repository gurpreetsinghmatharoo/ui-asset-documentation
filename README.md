# [GUI Pack with Theme Support (matharoo)](https://marketplace.yoyogames.com/assets/6500/gui-pack-with-theme-support)
## Documentation

Creating & managing UI elements is easier than ever!

## [Jump To GIFs](https://github.com/gurpreetsinghmatharoo/ui-asset-documentation/blob/master/README.md#gifs)
## [Jump To Examples](https://github.com/gurpreetsinghmatharoo/ui-asset-documentation/blob/master/README.md#examples)

# Note

Arguments inside [] are optional

# Elements
# Buttons

Use **button_create()** to create a button.

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

**button_clicked(id)** checks whether the button was clicked in this step.

### Example
```if (button_clicked(buttonBuy)) buyItem();```

## button_script()

Using **button_script(id, script)** you can assign a script to run each the button is 
clicked. It will automatically run whenever the button is pressed.

### Example
```button_script(buttonBuy, buyItem);```
        
## Button position

You can use a button's x/y variables to move it.

### Example
```buttonBuy.x = 256;```
        
```buttonBuy.y += 4;```

# Panels

Panels are rectangular areas that group elements inside them.

Use **panel_create()** to create a panel.

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

## Panel position

Use panel_pos(panel, x, y) to change a panel's position.

Use panel_move(panel, x+, y+) to add to the position of a panel.

# Text Fields

Use **textfield_create()** to create a single-line text field.

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

# Text Areas

Use **textarea_create()** to create a multi-line text area.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

## Text

You can use the `eText` variable to get the text in the text area. It'll return a string with a `#` to symbolize new lines.

You can also use `lineList` to get a DS list that contains strings for the lines in the text area.

### Example
```
var text = textArea.eText;
var lines = textArea.lineList;
var firstLine = ds_list_find_value(lines, 0);
```

## Options

Use **textarea_options()** to set some options for the text areas.

### Arguments

**id:** Text area ID to modify the options of. Use `all` to modify all text areas present at that time

**wrapping:** Should the text wrap to the next line when it reaches the end of the current one? *Default: false*

**dynamic_size:** Should the text area change its size according to the text inside it? *Default: true.*
                  If this is false, it will always stay the same size.

# Sliders

Use **slider_create()** to create a slider.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**[head_pos]:** initial position of the head, optional, 0-1

**[text]:** text to display, optional

***head_pos** is where position of the head on the slider, and it ranges from 0 to 1.*

## Head Position

Use the `headPos` variable to get the head position of a slider.
It will be in a 0 to 1 range.

### Example
```
var amount = sdAmount.headPos; //Gets the head position of the 'sdAmount' slider
```

# Check Boxes

Use **checkbox_create()** to create a checkbox.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**[text]:** text to display, optional

**[enabled]:** whether the check box is enabled. By default, it is not.

## Enabled

Use the variable **eEnabled** to get whether a check box is enabled or not. It can be modified too.

### Example
```
var enabled = checkbox.eEnabled;
```

# Radio Buttons

Use **radio_button_create()** to create a radio button.

### Arguments
**x:** x position

**y:** y position

**w:** width

**h:** height

**group_name:** Name of the radio group (string)

**[text]:** text to display, optional

## Radio Group

Use **radio_group_create()** to create a radio group, and **radio_group_delete()** to delete one.

### Arguments
**name:** name of the group (string)

You need a radio group to be able to create any radio buttons. Only one radio button inside a radio group can be selected.

### Example
```
radio_group_create("Food");
radio_button_create(8, 8, 32, 32, "Food", "Pasta");
radio_button_create(8, 40, 32, 32, "Food", "Pizza");
radio_button_create(8, 72, 32, 32, "Food", "Burger");
```

## Enabled

Just like the check box, you can use the **eEnabled** variable to get whether a radio button is selected or not.

You can also use the function **radio_group_get_selected(group_name)** to get the ID of the radio button instance, in that group, that is selected. It returns `noone` (-4) if no radio button is selected.

You can use the function **radio_toggle(id, true/false)** to change the state of a radio button.

# ---------------------------

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

# Size

You can change the size of an element by modifying its `eWidth` and `eHeight` variables.

### Example
```
var width_of_button = button.eWidth;

if (increase_panel_size){
  panel.eWidth += 32;
  panel.eHeight += 32;
}
```

# Destroying

Use `instance_destroy(id)` to destroy UI elements you create.

Destroying panels will also destroy the elements inside them.

# Theme

You can change the theme by using **ui_theme(theme)**.

There are three themes: `theme.Material`, `theme.HQ` and `Theme.Pixel`. HQ is the default theme.

### Example
```
ui_theme(theme.Material); //Changes theme to Material
```

# Sprites

Use `ui_sprite()` to change the sprites for every type of element in a theme.

### Arguments:
**Theme:** Theme to edit

**Buttons:** Sprite for buttons

**Panels:** Sprite for panels

**Text Field:** Sprite for text fields

**Slider:** Sprite for sliders

**Checkbox:** Sprite for checkbox

**Checktick:** Sprite for checkbox tick (enabled symbol)

**Radiobuttons:** Sprite for radio button (circle, two subimages: first disabled, second enabled)

Look at the default sprites for reference.

If you don't want to change the sprite for any of these arguments, just pass -1.

# Options

Use `ui_theme_options()` to change the options for a theme.

### Arguments:
**Theme:** Theme to edit

**Color:** Color for the elements

**Font Color:** Font color for the text

### Example
```
ui_theme_options(theme.Pixel, c_orange, c_blue); //Changes element color to orange and font color to blue, for the Pixel theme
```

# GIFs

## Panel with three buttons

![Panels](https://i.imgur.com/nN8HgNw.gif)

## Text Field

![Text Field](https://i.imgur.com/xHJy4sX.gif)

## Text Area

![Text Area](https://i.imgur.com/pCotpKL.gif)

## Slider & Checkbox

![Slider & Checkbox](https://i.imgur.com/S001OGB.gif)

# Examples

## Creating a text dialog window

Using this GUI pack, you can easily create text dialog windows, to get user input.

Here's how you would create one:
```java
//Window position
var _x, _y, _w, _h;
_x = 320;
_y = 200;
_w = 200;
_h = 128;

//Create elements
dialogPanel = panel_create(_x, _y, _w, _h, "Enter Name");
dialogTextField = textfield_create(_x+8, _y+36, _w-16, 32);
dialogButton = button_create(_x+32, (_y+_h)-48, _w-64, 32, "OK");

panel_add(dialogPanel, dialogTextField, dialogButton);

//Store element IDs
dialogButton.myPanel = dialogPanel;
dialogButton.myTextField = dialogTextField;

//Assign script
button_script(dialogButton, dialog_button_script);
```

I first set the position and size for the dialog window, then created the elements, and added them in the panel. Then I initialized variables inside the button, to store the IDs of the panel & textfield, so that it knows which dialog elements it belongs to. Then I'm assigning a script to the button.

This is that script:
```
//Set window caption to the text
window_set_caption(myTextField.eText);

//Destroy
instance_destroy(myPanel);
```

It sets the window's caption to the text entered in the dialog text field, then destroys the panel (which automatically destroys all the elements inside it). Changing the window's caption is just an example, to show that you can retrieve the text field's text in the button script.

![GIF](https://i.imgur.com/kXsZi9q.gif)

Of course, if you don't want the panel to be destroyed when the button is clicked, remove the `instance_destroy(myPanel)` statement from the script.
