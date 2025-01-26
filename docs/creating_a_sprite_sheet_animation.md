[← Back to Index](index.md)

## Creating a Sprite Sheet Animation

The following code shows how to create a sprite sheet animation in a MonoGame project:

This code snippet demonstrates how to create a sprite sheet animation in a MonoGame project. A sprite sheet is a single image file that contains multiple frames of an animation. By specifying the source rectangle for each frame, you can animate the sprite by changing the displayed frame over time.

```csharp
protected override void Update(GameTime gameTime)
{
	elapsedTime += (float)gameTime.ElapsedGameTime.TotalMilliseconds;
	if (elapsedTime >= delay)
	{
		currentFrame++;
		if (currentFrame >= totalFrames)
			currentFrame = 0;
		elapsedTime = 0;
	}
	base.Update(gameTime);
}

protected override void Draw(GameTime gameTime)
{
	GraphicsDevice.Clear(Color.CornflowerBlue);
	_spriteBatch.Begin();
	_spriteBatch.Draw(texture, position, sourceRect, Color.White);
	_spriteBatch.End();
	base.Draw(gameTime);
}
```

[← Back to Index](index.md)