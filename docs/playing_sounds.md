[← Back to Index](index.md)

## Playing Sounds

The following code shows how to play sounds in a MonoGame project:

This code snippet demonstrates how to play sounds in a MonoGame project. The `SoundEffect` and `SoundEffectInstance` classes are used to load and play sound effects. You can load a sound effect from a file and create an instance to play it with options for volume, pitch, and looping.

```csharp
protected override void LoadContent()
{
	soundEffect = Content.Load<SoundEffect>("sound");
	soundEffectInstance = soundEffect.CreateInstance();
	soundEffectInstance.IsLooped = true;
	soundEffectInstance.Play();
}
```

[← Back to Index](index.md)