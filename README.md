# Unnamed GUI Asset (matharoo)
## Documentation

Creating & managing UI elements is easier than ever!

# Note

Arguments inside [] are optional

## GUI Mode

Use ui_gui_mode(true/false) to enable/disable GUI mode.
Default: true

With GUI mode on, the UI will be drawn on the screen/GUI layer.
Without GUI mode, it will be drawn inside the room.

## Manual Placement

If you don't want to use code and want to manually place the UI elements
in the room, you can do so. But, you will need to fill in some variables
in those instances' Creation Codes.

For that particular element, open its create script (for example, 'button_create'
for buttons) and go to the '//Set variables' part. See which variables
are being set, and initialize them in the Creation Code.

Of course, you don't need to do this if you *are* using the scripts.

Also, the elements you place using the room editor are not drawn to
the GUI layer.

## Destroying

Use instance_destroy(id) to destroy UI elements you create.

# Buttons

Use button_create() to create a button.

### Arguments
x: x position

y: y position

w: width

h: height

text: text to display

[animate]: whether to enable effects on the button
           default: true

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

# PANELS

Panels are rectangular areas that group buttons inside them.

Use panel_create() to create a panel.

### Arguments
x: x position

y: y position

w: width

h: height

[text]: text to display
        
Store the returned id in a variable.

    Example:
        panelMain = panel_create(8, 8, 256, 128, "Main");
        
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


