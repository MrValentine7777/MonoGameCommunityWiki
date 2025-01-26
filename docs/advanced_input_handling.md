[← Back to Index](index.md)

## Advanced Input Handling

The following code demonstrates how to implement a robust input handling system with key repeat prevention:

This code creates an InputManager class that:
- Tracks both current and previous keyboard/gamepad states
- Prevents repeated key presses until key is released
- Provides methods to check if keys were just pressed or released
- Handles both keyboard and gamepad input in a unified way
- Uses a singleton pattern for easy access throughout the game

```csharp
public class InputManager
{
    // Singleton instance
    private static InputManager _instance;
    public static InputManager Instance
    {
        get
        {
            if (_instance == null)
                _instance = new InputManager();
            return _instance;
        }
    }

    // Current and previous input states
    private KeyboardState _currentKeyboardState;
    private KeyboardState _previousKeyboardState;
    private GamePadState _currentGamePadState;
    private GamePadState _previousGamePadState;
    
    // Dictionary to track locked keys
    private Dictionary<Keys, bool> _keyLocks;
    private Dictionary<Buttons, bool> _buttonLocks;

    public InputManager()
    {
        _keyLocks = new Dictionary<Keys, bool>();
        _buttonLocks = new Dictionary<Buttons, bool>();
    }

    // Update input states
    public void Update()
    {
        _previousKeyboardState = _currentKeyboardState;
        _previousGamePadState = _currentGamePadState;
        
        _currentKeyboardState = Keyboard.GetState();
        _currentGamePadState = GamePad.GetState(PlayerIndex.One);
    }

    // Check if a key was just pressed (with repeat prevention)
    public bool IsKeyPressed(Keys key)
    {
        // Initialize lock state if not present
        if (!_keyLocks.ContainsKey(key))
            _keyLocks[key] = false;

        // Check if key was just pressed and not locked
        if (_currentKeyboardState.IsKeyDown(key) && 
            _previousKeyboardState.IsKeyUp(key) && 
            !_keyLocks[key])
        {
            _keyLocks[key] = true;
            return true;
        }

        // Remove lock when key is released
        if (_currentKeyboardState.IsKeyUp(key))
            _keyLocks[key] = false;

        return false;
    }

    // Check if a button was just pressed (with repeat prevention)
    public bool IsButtonPressed(Buttons button)
    {
        if (!_buttonLocks.ContainsKey(button))
            _buttonLocks[button] = false;

        if (_currentGamePadState.IsButtonDown(button) && 
            _previousGamePadState.IsButtonUp(button) && 
            !_buttonLocks[button])
        {
            _buttonLocks[button] = true;
            return true;
        }

        if (_currentGamePadState.IsButtonUp(button))
            _buttonLocks[button] = false;

        return false;
    }

    // Check if a key is being held down
    public bool IsKeyHeld(Keys key)
    {
        return _currentKeyboardState.IsKeyDown(key);
    }

    // Check if a button is being held down
    public bool IsButtonHeld(Buttons button)
    {
        return _currentGamePadState.IsButtonDown(button);
    }

    // Get thumbstick values
    public Vector2 LeftThumbStick
    {
        get { return _currentGamePadState.ThumbSticks.Left; }
    }

    public Vector2 RightThumbStick
    {
        get { return _currentGamePadState.ThumbSticks.Right; }
    }
}
```

Usage example in your game class:

```csharp
public class Game1 : Game
{
    private InputManager _input;

    protected override void Initialize()
    {
        _input = InputManager.Instance;
        base.Initialize();
    }

    protected override void Update(GameTime gameTime)
    {
        // Update input states
        _input.Update();

        // Check for single press actions
        if (_input.IsKeyPressed(Keys.Space) || _input.IsButtonPressed(Buttons.A))
        {
            // Handle jump action - will only trigger once per press
            Jump();
        }

        // Check for held actions
        if (_input.IsKeyHeld(Keys.Left) || _input.IsButtonHeld(Buttons.DPadLeft))
        {
            // Handle continuous movement
            MoveLeft();
        }

        // Get analog input
        Vector2 movement = _input.LeftThumbStick;
        if (movement != Vector2.Zero)
        {
            // Handle analog movement
            MovePlayer(movement);
        }

        base.Update(gameTime);
    }
}
```

This input handling system provides several benefits:
1. Prevents unintended repeat actions from held keys
2. Clearly separates single-press and held-key actions
3. Handles both keyboard and gamepad input consistently
4. Provides analog input support for smooth movement
5. Uses singleton pattern for easy access across game classes
6. Maintains clean and organized input state management

The system is particularly useful for:
- Menu navigation where you want single button presses
- Action games where precise input timing is important
- Games that need to support both keyboard and gamepad
- Any situation where you need to prevent key repeat

[← Back to Index](index.md)