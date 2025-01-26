# Code Samples

Here are some useful code samples to help you get started with MonoGame development.

## Basic Game Loop

The following code shows the basic structure of a MonoGame project's main game class:

This template includes the essential components of a MonoGame project:

- **Constructor**: Initializes the graphics device manager and sets the content directory
- **Initialize**: Called once when the game starts, use this for non-graphics initialization
- **LoadContent**: Called once when the game starts, load your textures and other content here
- **Update**: Called every frame, update your game logic here (input, physics, AI, etc.)
- **Draw**: Called every frame, render your game graphics here

The game loop automatically calls Update and Draw in sequence to create the game's runtime cycle. The `GameTime` parameter provides timing information for frame-rate independent game logic.

```csharp
// The following code is a C# code block
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;
using Microsoft.Xna.Framework.Input;

namespace MyGame
{
	public class Game1 : Game
	{
		private GraphicsDeviceManager _graphics;
		private SpriteBatch _spriteBatch;
		public Game1()
		{
			_graphics = new GraphicsDeviceManager(this);
			Content.RootDirectory = "Content";
		}
		protected override void Initialize()
		{
			base.Initialize();
		}
		protected override void LoadContent()
		{
			_spriteBatch = new SpriteBatch(GraphicsDevice);
		}
		protected override void Update(GameTime gameTime)
		{
			if (GamePad.GetState(PlayerIndex.One).Buttons.Back == 
			ButtonState.Pressed || 
			Keyboard.GetState().IsKeyDown(Keys.Escape))
				Exit();
			base.Update(gameTime);
		}
		protected override void Draw(GameTime gameTime)
		{
			GraphicsDevice.Clear(Color.CornflowerBlue);
			base.Draw(gameTime);
		}
	}
}
```

## Anatomy of a MonoGame project

The following code shows the detailed structure of a MonoGame project, including comprehensive setup options and explanations for each component:

This template demonstrates a complete MonoGame project structure with the following key features:

1. **Graphics Configuration**
   - BackBuffer resolution setting
   - Fullscreen toggle
   - VSync control
   - Graphics device management

2. **Game Loop Methods**
   - Initialize: For non-graphics initialization
   - LoadContent: For loading game assets
   - Update: For game logic (60 times per second by default)
   - Draw: For rendering graphics
   - UnloadContent: For cleanup

3. **Game State Management**
   - Basic state enum
   - State-specific update and draw methods
   - Clean separation of concerns

4. **Input Handling**
   - Keyboard and gamepad state checking
   - Frame-independent timing
   - Exit game functionality

5. **Content Pipeline Integration**
   - Content manager setup
   - Example content loading patterns
   - Resource management

The code includes extensive comments explaining each section's purpose and usage, making it ideal for beginners to understand the structure of a MonoGame project. You can use this as a starting point and modify it according to your game's specific needs.

```csharp
// The following code is a C# code block
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;
using Microsoft.Xna.Framework.Input;

namespace MyGame
{
	public class Game1 : Game
	{
		private GraphicsDeviceManager _graphics;
		private SpriteBatch _spriteBatch;
		private enum GameState { MainMenu, Playing, Paused, GameOver }
		private GameState _gameState = GameState.MainMenu;
		public Game1()
		{
			_graphics = new GraphicsDeviceManager(this);
			Content.RootDirectory = "Content";
			IsMouseVisible = true;
		}
		protected override void Initialize()
		{

		base.Initialize();
		}

		protected override void LoadContent()
		{
			_spriteBatch = new SpriteBatch(GraphicsDevice);
		}

		protected override void UnloadContent()
		{
		}

		protected override void Update(GameTime gameTime)
		{
			if (GamePad.GetState(PlayerIndex.One).Buttons.Back ==
				ButtonState.Pressed ||
				Keyboard.GetState().IsKeyDown(Keys.Escape))
					Exit();
			switch (_gameState)
			{
				case GameState.MainMenu:
					UpdateMainMenu(gameTime);
					break;
				case GameState.Playing:
					UpdatePlaying(gameTime);
					break;
				case GameState.Paused:
					UpdatePaused(gameTime);
					break;
				case GameState.GameOver:
					UpdateGameOver(gameTime);
					break;
			}
			base.Update(gameTime);
		}

		protected override void Draw(GameTime gameTime)
		{
			GraphicsDevice.Clear(Color.CornflowerBlue);
			_spriteBatch.Begin();
			switch (_gameState)
			{
				case GameState.MainMenu:
					DrawMainMenu(gameTime);
					break;
				case GameState.Playing:
					DrawPlaying(gameTime);
					break;
				case GameState.Paused:
					DrawPaused(gameTime);
					break;
				case GameState.GameOver:
					DrawGameOver(gameTime);
					break;
			}
			_spriteBatch.End();
			base.Draw(gameTime);
		}

		private void UpdateMainMenu(GameTime gameTime)
		{
			// Update main menu logic
		}

		private void UpdatePlaying(GameTime gameTime)
		{
			// Update playing logic
		}

		private void UpdatePaused(GameTime gameTime)
		{
			// Update paused logic
		}

		private void UpdateGameOver(GameTime gameTime)
		{
			// Update game over logic
		}

		private void DrawMainMenu(GameTime gameTime)
		{
			// Draw main menu graphics
		}

		private void DrawPlaying(GameTime gameTime)
		{
			// Draw playing graphics
		}

		private void DrawPaused(GameTime gameTime)
		{
			// Draw paused graphics
		}

		private void DrawGameOver(GameTime gameTime)
		{
			// Draw game over graphics
		}
	}
}
```

## Drawing a Sprite

The following code shows how to draw a sprite on the screen using a `Texture2D` object:

This code snippet demonstrates how to draw a sprite on the screen using a `Texture2D` object. The `SpriteBatch` class is used to draw 2D graphics in MonoGame. The `Draw` method takes a `Texture2D` object, a position vector, and an optional color parameter. The `Begin` and `End` methods are used to start and finish the drawing process.

```csharp
// The following code is a C# code block
protected override void Draw(GameTime gameTime)
{
	GraphicsDevice.Clear(Color.CornflowerBlue);
	_spriteBatch.Begin();
	_spriteBatch.Draw(texture, position, Color.White);
	_spriteBatch.End();
	base.Draw(gameTime);
}
```

## Handling Input

The following code shows how to handle input in a MonoGame project:

This code snippet demonstrates how to handle input in a MonoGame project. The `Keyboard` and `GamePad` classes provide access to keyboard and gamepad input, respectively. You can check for specific keys or buttons being pressed, released, or held down to control your game logic.

```csharp
// The following code is a C# code block
protected override void Update(GameTime gameTime)
{
	if (GamePad.GetState(PlayerIndex.One).Buttons.Back == 
		ButtonState.Pressed || 
		Keyboard.GetState().IsKeyDown(Keys.Escape))
		Exit();
	base.Update(gameTime);
}
```

## Loading Content

The following code shows how to load content in a MonoGame project:

This code snippet demonstrates how to load content in a MonoGame project. The `ContentManager` class is used to load and manage game assets such as textures, fonts, and sounds. You can load content by specifying the asset file path and type, and then access it using the `Content` property.

// The following code is a C# code block
protected override void LoadContent()
{
	texture = Content.Load<Texture2D>("sprite");
}

## Playing Sounds

The following code shows how to play sounds in a MonoGame project:

This code snippet demonstrates how to play sounds in a MonoGame project. The `SoundEffect` and `SoundEffectInstance` classes are used to load and play sound effects. You can load a sound effect from a file and create an instance to play it with options for volume, pitch, and looping.

```csharp
// The following code is a C# code block
protected override void LoadContent()
{
	soundEffect = Content.Load<SoundEffect>("sound");
	soundEffectInstance = soundEffect.CreateInstance();
	soundEffectInstance.IsLooped = true;
	soundEffectInstance.Play();
}
```

## Creating a Sprite Sheet Animation

The following code shows how to create a sprite sheet animation in a MonoGame project:

This code snippet demonstrates how to create a sprite sheet animation in a MonoGame project. A sprite sheet is a single image file that contains multiple frames of an animation. By specifying the source rectangle for each frame, you can animate the sprite by changing the displayed frame over time.

```csharp
// The following code is a C# code block
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

## Implementing Collision Detection

The following code shows how to implement collision detection in a MonoGame project:

This code snippet demonstrates how to implement collision detection in a MonoGame project. You can check for collisions between game objects by comparing their bounding boxes or shapes. By using methods like `Intersects` or `Contains`, you can detect when objects overlap and respond accordingly.

```csharp
// The following code is a C# code block
protected override void Update(GameTime gameTime)
{
	if (playerRect.Intersects(enemyRect))
	{
		// Handle collision
	}
	base.Update(gameTime);
}
```

## Implementing a Camera

The following code shows how to implement a camera in a MonoGame project:

This code snippet demonstrates how to implement a camera in a MonoGame project. A camera is used to control the view of the game world and can be moved, rotated, or zoomed to focus on different areas. By adjusting the camera's position and projection matrix, you can create scrolling, zooming, or parallax effects.

```csharp
// The following code is a C# code block
protected override void Update(GameTime gameTime)
{
	camera.Position = player.Position - 
		new Vector2(GraphicsDevice.Viewport.Width / 2,
			GraphicsDevice.Viewport.Height / 2);
	base.Update(gameTime);
}

protected override void Draw(GameTime gameTime)
{
	GraphicsDevice.Clear(Color.CornflowerBlue);
	_spriteBatch.Begin(transformMatrix: camera.GetViewMatrix());
	// Draw game objects
	_spriteBatch.End();
	base.Draw(gameTime);
}
```

These code samples cover some of the essential aspects of MonoGame development, including the game loop, drawing sprites, handling input, loading content, playing sounds, creating animations, implementing collision detection, and using a camera. You can use these examples as a starting point for your own MonoGame projects and customize them to suit your game's requirements.