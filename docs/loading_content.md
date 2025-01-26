[← Back to Index](index.md)

## Loading Content

The following code shows how to load content in a MonoGame project:

This code snippet demonstrates how to load content in a MonoGame project. The `ContentManager` class is used to load and manage game assets such as textures, fonts, and sounds. You can load content by specifying the asset file path and type, and then access it using the `Content` property.

```csharp
protected override void LoadContent()
{
	texture = Content.Load<Texture2D>("sprite");
}
```

[← Back to Index](index.md)