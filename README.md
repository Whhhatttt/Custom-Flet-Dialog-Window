# Custom-Flet-Dialog-Window
![image](https://github.com/Whhhatttt/Custom-Flet-Dialog-Window/assets/40802556/262e0f4c-68d0-41ff-b403-ba96d1884d47)


![image](https://github.com/Whhhatttt/Custom-Flet-Dialog-Window/assets/40802556/a6705c36-2224-4db6-89c3-cdabd93f1820)


Overall it was not a difficult project. But it still requires work. Some things can be improved, some things can be optimized. Feel free to suggest your own edits or more convenient functionality.


## Features
- Customizable dialog window with various options for size, theme, actions, content, and more.
- Ability to add custom actions buttons to the dialog window.
- Default parameters for easy customization, including default dark theme, actions alignment, content alignment, and more.

### Import UI_DialogWindow into your project.


### main.py
```
import flet as ft
from UI_DialogWindow import DialogWindow


class main_app:
     def __init__(self,page: ft.Page):
         super().__init__()
         self.page = page
         self.page.theme_mode = ft.ThemeMode.DARK
         self.page.window_height = 1000
         self.page.window_width = 1200
         self.page.window_full_screen = False
         self.page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
         self.page.vertical_alignment = ft.MainAxisAlignment.CENTER
         self.main()
     def show_dialog(self,e):
             def on_click(e): # ON CLICK ACTION
                 print('lets go')
             icon = ft.Icon(ft.icons.ERROR,color='red',size=100)
            
             dialog_ = DialogWindow(
                  width=500,
                  content=icon,
                  mode_theme=self.page.theme_mode)
            
             self.page.dialog = dialog_
             self.page.update()
             dialog_.show()
     def main(self):
         self.page.add(ft.TextButton(text='Test Dialog',on_click=self.show_dialog))
         self.page.add(ft.Text('LOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOL'))
         self.page.update()
         self.show_dialog('f')


def main(page: ft.Page):
     main_app(page=page)
ft.app(main)
```

### We can also add our own Actions Buttons:

```
def show_dialog(self,e):
     def on_click(e): # ON CLICK ACTION
         print('lets go')
     icon = ft.Icon(ft.icons.ERROR,color='red',size=100)
    
     dialog_ = DialogWindow(
          width=500,
          content=icon,
          mode_theme=self.page.theme_mode,
          actions=[ft.TextButton('OK',on_click=on_click),ft.TextButton('CANCEL',on_click=on_click)] #HERE IS
          )
    
     self.page.dialog = dialog_
     self.page.update()
     dialog_.show()
```


### Default class parameters:

```
width=400,
                 
mode_theme = ft.ThemeMode.DARK,                                   #by default we have a dark theme.
                                                                   Change this parameter by inserting ft.ThemeMode.LIGHT
                                                                   or just page.self.theme_mode here as shown in the example above.

actions=[],                                                       # by default we have 1 OK button
actions_alignment = ft.MainAxisAlignment.CENTER,                  # positioning action buttons

content=None,                                                     # content of dialog window
content_padding = 10,                                             # padding from edge
content_alignment = ft.alignment.center,                          # positioning content inside the Windows dialog

title='Dialog',
title_alignment=ft.alignment.top_left,
title_padding = 20,
title_size = 25,

bgcolor_dialog_dark = 'black,0.2',                                #color of dialog window will be used if the theme is DARK
bgcolor_dialog_light = 'white,0.8',                               #color of dialog window will be used if the theme is LIGHT

blur_size = [5,5]                                                 #blur size x; y;
```



### Known problems:
- poor vertical positioning of the window
- impossible to add containers with ```on_click``` parameters to ```actions```

### Please! Suggest your edits and solutions to some problems. As well as improving this DialogWindow
