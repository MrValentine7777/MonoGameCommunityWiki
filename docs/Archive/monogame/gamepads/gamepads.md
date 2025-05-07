====== GamePads ======

This page will be added to with more code samples and usability.

[ADDMORE: Include the guide on GamePad.GetState(int) to allow using more than four gamepads]

==== Preventing Repeated Code ====

The following code is how you prevent a button press repeating.

Required using statements:

```csharp
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Content;
using Microsoft.Xna.Framework.Graphics;
using Microsoft.Xna.Framework.Input;
using System.Diagnostics;
```

You need a global variable per button:

```csharp
// global variables
// Using a boolean flag to check if the A button is being held down
// true if it is, false if it is not
bool p1AButtonDown = false;
```

The code required:

```csharp
GamePadState PlayerOne = GamePad.GetState(PlayerIndex.One);
if (PlayerOne.IsConnected)
{
    // Inside the update method, check for A button press and release
    if (PlayerOne.Buttons.A == ButtonState.Pressed && !p1AButtonDown)
    {
        p1AButtonDown = true;
        // Code for A button press
        Debug.WriteLine(PlayerOne);
    }
    else if (PlayerOne.Buttons.A == ButtonState.Released && p1AButtonDown)
    {
        p1AButtonDown = false;
        // Code for A button release (if needed)
    }
}
```

[ADDMORE: Code required to handle the sticks and triggers]

==== GamePad States ====

Below is the gamepad states:

```csharp
[
GamePadState:
IsConnected=1, // 1 means connected, 0 means not connected
PacketNumber=1362033298, 
// A signed value, can be a negative value as well as positive
// This value is an example
// Typically used for networking
Buttons=
[
GamePadButtons: 
A=1, 
// Showing 1 as this is the button used to trigger the printout
B=0, 
Back=0, 
X=0, 
Y=0, 
Start=0, 
LeftShoulder=0, 
LeftStick=0, // When you press the Left stick in
RightShoulder=0, 
RightStick=0, // When you press the Right stick in
BigButton=0 
// Honestly no idea what this is so ignore it
// but it could be related to this:
// https://github.com/sverrirs/XboxBigButton
// https://blog.sverrirs.com/2015/10/how-to-use-xbox-360-big-button.html
],
DPad=0000, // UP=0100 DOWN=0001 LEFT=1000 RIGHT=0010
ThumbSticks=
[
GamePadThumbSticks: 
Left={X:0 Y:0},
// Remember these values are signed values
// For example full left is -1, so -0.25 is one quarter to the left
// and the inverse is 1, so 0.25 is one quarter to the right
// Up is a positive value to 1, and down is a negative value to -1
Right={X:0 Y:0}
// Remember these values are signed values
// For example full left is -1, so -0.25 is one quarter to the left
// and the inverse is 1, so 0.25 is one quarter to the right
// Up is a positive value to 1, and down is a negative value to -1
], 
Triggers=
[
GamePadTriggers: // The Left and Right pressure triggers
Left=0, 
// An unsigned float value from 0 to 1
// For example, half way is represented by 0.5
Right=0 
// An unsigned float value from 0 to 1
// For example, half way is represented by 0.5
]
]
```

The above layout was copied from printing the PlayerOne values as the following code demonstrates:


[ADDMORE: The following code needs to be updated with the single press code]

```csharp
GamePadState PlayerOne = GamePad.GetState(PlayerIndex.One);
if (PlayerOne.IsConnected)
{
    if (PlayerOne.Buttons.A == ButtonState.Pressed)
    {
        Debug.WriteLine(PlayerOne);
    }
}
```

Which spits out a single line as below:

```csharp
[
GamePadState: 
IsConnected=1, 
PacketNumber=-451982739, 
Buttons=
[
GamePadButtons: 
A=1, 
B=0, 
Back=0, 
X=0, 
Y=0, 
Start=0, 
LeftShoulder=0, 
LeftStick=0, 
RightShoulder=0, 
RightStick=0, 
BigButton=0], 
DPad=0000, 
ThumbSticks=
[GamePadThumbSticks:
Left={X:0 Y:0},
Right={X:0 Y:0}],
Triggers=
[GamePadTriggers:
Left=0, 
Right=0
]
]
```