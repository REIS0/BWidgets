# B.Widgets

**Stop: This branch contains the old B.Widgets (without an official API). Take a look at the new B.Widgets API at the [devel](https://github.com/sjaehn/BWidgets/tree/devel) branch.**

Widget toolkit based on Cairo and PUGL.

This is a simple widget toolkit for the B.Music projects.

**This toolkit is still in development**

Dependencies
------------
* Cairo
* X11 (for Linux systems, for MacOS X and Windows see description)

Install the developers versions of these packages first. BWidgets may also be adapted to MacOS X and Windows. For these systems, take hands on and adapt the final parameter in line 2 of the makefile.

Installation
------------
Clone this repository. To build the demo simply call

```
make
```
from the root directory of the clone.

Run the demo
------------
Simply call

```
./demo
```

Usage
-----
BWidgets is a toolkit intended to use directly in B.Music projects. If you want to use it, simply copy the BWidgets folder (includig its subfolders) into your project folder. Remove the widgets you don't need, but take care for dependencies.

Class hierarchy
---------------
```
namespace BUtilities
 ├── Point
 ├── RectArea
 ╰── Any

namespace BColors
 ├── Color
 ╰── ColorSet

namespace BStyles
 ├── Line
 ├── Border
 ├── Fill
 ├── Font
 ├── Style
 ├── StyleSet
 ╰── Theme

namespace BDevices
 ├── MouseDevice
 ├── DeviceGrab
 ╰── DeviceGrabStack

namespace BEvents
 ╰── Event
      ├── WidgetEvent
      │    ╰── ExposeEvent
      ├── KeyEvent
      ├── PointerEvent
      ├── WheelEvent
      ├── FocusEvent
      ├── ValueChangedEvent
      ╰── MessageEvent

namespace BItems
 ├── Item
 ╰── ItemList

namespace BWidgets
 ├── Focusable
 ╰── Widget
      ├── Window
      ├── DrawingSurface
      ├── Display
      │    ╰── StateDisplay
      ├── Icon
      │    ╰── ImageIcon
      ├── Label
      ├── Text
      ├── Knob
      ├── ValueWidget
      │    ├── Button
      │    │    ├── UpButton
      │    │    ├── DownButton
      │    │    ├── LeftButton
      │    │    ├── RightButton
      │    │    ├── PlusButton
      │    │    ├── MinusButton
      │    │    ├── TextButton
      │    │    ╰── ToggleButton
      │    │         ╰── TextToggleButton
      │    ├── MessageBox
      │    ├── FileChooser
      │    ├── ItemBox
      │    │    ╰── PopupListBox
      │    ├── ChoiceBox
      │    │    ╰── ListBox
      │    ╰── RangeWidget
      │         ├── Dial
      │         │    ╰── DialValue
      │         ├── HScale
      │         │    ╰── HSlider
      │         │         ├── HSwitch
      │         │         ╰── HSliderValue
      │         ╰── VScale
      │              ╰── VSlider
      │                   ├── VSwitch
      │                   ╰── VSliderValue
      ╰── PianoWidget
           ╰── HPianoRoll

```

Widgets
-------

All widget classes of BWidgets are derived from **BWidgets::Widget**. This widget class contain all important basic widget informations, such as position in the widget tree (children, parent, main), position on screen (relative to its parent widget), size, border, background, visibility and their ability to emit events (clickability, draggability, scrollability, focusability). Thus, all derived widget inherit and may extend these properties.

The most important class of BWidgets is **BWidgets::Window**. An object of this class is not only the main window to add all other widget to. Is also hosts the event handler and represents the connection to the system. Therefore, only one BWidgets::Window is allowed.

**BWidgets::ValueWidget** extends BWidgets::Widgets by a value and their ability to emit ValueChangedEvents.

In **BWidgets::RangeWidget**, the value is additionally kept within a defines range.
