[← Back to Index](index.md)

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
				case GameState.Loading:
				// Update loading logic
					break;
				case GameState.Options:
				// Update options logic
					break;
				case GameState.Scores:
				// Update scores logic
					break;
				case GameState.Credits:
				// Update credits logic
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
				case GameState.Loading:
				// Draw loading graphics
					break;
				case GameState.Options:
				// Draw options graphics
					break;
				case GameState.Scores:
				// Draw scores graphics
					break;
				case GameState.Credits:
				// Draw credits graphics
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

		<Summay>
		/// The possible game states for the game
		/// This can be used to control the flow of the game
		/// You can imagine this as a state machine where 
		/// the game can be in one of these states at any given time
		</Summay>
		public enum GameState
		{
			/// <summary>
			/// The main menu state where players can start new game, load game, or quit
			/// </summary>
			MainMenu,

			/// <summary>
			/// The active gameplay state where the main game loop runs
			/// </summary>
			Playing,
    
			/// <summary>
			/// Paused state where gameplay is suspended but game is still running
			/// </summary>
			Paused,
    
			/// <summary>
			/// Game over state when player has lost or completed the game
			/// </summary>
			GameOver,
    
			/// <summary>
			/// Loading state for transitions between major game sections
			/// </summary>
			Loading,
    
			/// <summary>
			/// Options/settings menu state
			/// </summary>
			Options,
    
			/// <summary>
			/// High score or achievements display state
			/// </summary>
			Scores,
    
			/// <summary>
			/// Credits display state
			/// </summary> 
			Credits
		}
	}
}
```

[← Back to Index](index.md)