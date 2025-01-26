[← Back to Index](index.md)

## Basic Game Loop

The following code shows the basic structure of a MonoGame project's main game class:

This template includes the essential components of a MonoGame project:

- **Constructor**: Initializes the graphics device manager and sets the content directory
- **Initialize**: Called once when the game starts, use this for non-graphics initialization
- **LoadContent**: Called once when the game starts, load your textures and other content here
- **Update**: Called every frame, update your game logic here (input, physics, AI, etc.)
- **Draw**: Called every frame, render your game graphics here

The game loop automatically calls Update and Draw in sequence to create the game's runtime cycle. The `GameTime` parameter provides timing information for frame-rate independent game logic.

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

This template provides a starting point for your MonoGame project. You can add additional functionality to the `Update` and `Draw` methods to create your game logic and graphics rendering.

For more advanced game development topics, refer to the other guides in the documentation.

[← Back to Index](index.md)

