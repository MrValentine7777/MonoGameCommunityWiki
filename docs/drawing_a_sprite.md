# Drawing a Sprite

The following code shows how to draw a sprite on the screen using a `Texture2D` object:

This code snippet demonstrates how to draw a sprite on the screen using a `Texture2D` object. The `SpriteBatch` class is used to draw 2D graphics in MonoGame. The `Draw` method takes a `Texture2D` object, a position vector, and an optional color parameter. The `Begin` and `End` methods are used to start and finish the drawing process.

```csharp
protected override void Draw(GameTime gameTime)
{
	GraphicsDevice.Clear(Color.CornflowerBlue);
	_spriteBatch.Begin();
	_spriteBatch.Draw(texture, position, Color.White);
	_spriteBatch.End();
	base.Draw(gameTime);
}
```

In this code snippet, `texture` is a `Texture2D` object representing the sprite image, and `position` is a `Vector2` object representing the position on the screen where the sprite will be drawn. The `Color.White` parameter specifies the color tint of the sprite (in this case, no tint is applied).

To load a `Texture2D` object from an image file, you can use the following code:
```csharp
Texture2D texture = Content.Load<Texture2D>("sprite");
```

You would perform this step in the `LoadContent` method of your `Game` class.

This code snippet loads a `Texture2D` object named "sprite" from the content pipeline. The image file should be placed in the Content folder of the project and added to the content pipeline using the MonoGame Content Pipeline tool.

By following these steps, you can draw a sprite on the screen in a MonoGame project.