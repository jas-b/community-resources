---
name: Color Selector
creator: Jason Brand
license: mit
link: https://github.com/jas-b/color_select_lib/
language: c
---

##Description
This library opens a seperate window for color selections.
Useful for converting existing apps to color.

##Usage

#### 1. Add color_sel_lib.h and color_sel_lib.c to your Pebble project.
```c
#include "color_sel_lib.h"
```
#### 2. Define a handler to get the entered color:
```c
void handle_CS_close(int color_argb) {
  GColor color.argb = color_argb;
  // Do something
  
  // or use directly
  text_layer_set_background_color(text_layer_name, (GColor){.argb = color_argb});
}
```
#### 3. Create the window and show it:
```c
CSWindow * myCSWindow = cswindow_create(
  default_color, false, 
  (CSCloseHandler)handle_CS_close);

cswindow_show(myCSWindow, true);
```

|Parameter|Description|
|---|---|
|**default_color**|The default color that the window will try to match. This may be null.|
|**full_palette**|true to use all 64 color, false to use a subset of 11 main colors. This may be null.|
|**closeHandler**|The CSCloseHandler to fire when the keyboard closes. This may be null.|