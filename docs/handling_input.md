## Handling Input

The following code shows how to handle input in a MonoGame project:

This code snippet demonstrates how to handle input in a MonoGame project. The `Keyboard` and `GamePad` classes provide access to keyboard and gamepad input, respectively. You can check for specific keys or buttons being pressed, released, or held down to control your game logic.

```csharp
protected override void Update(GameTime gameTime)
{
	if (GamePad.GetState(PlayerIndex.One).Buttons.Back == 
		ButtonState.Pressed || 
		Keyboard.GetState().IsKeyDown(Keys.Escape))
		Exit();
	base.Update(gameTime);
}
```