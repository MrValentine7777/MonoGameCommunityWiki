# Getting Started with MonoGame

This guide will help you set up your first MonoGame project.

## Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download)
- [MonoGame Setup](https://docs.monogame.net/articles/getting_started/index.html)

## Creating a New Project

1. Open your terminal or command prompt.
2. Run the following command:
```bash
dotnet new mgdesktopgl -n MyGame
```

Or for Desktop DirectX: [If you will only target Windows systems.]

```bash
dotnet new mgdesktopdx -n MyGame
```

3. Navigate to the project directory:
```bash
cd MyGame
```

4. Open the project in your preferred code editor:
```bash
code .
```

## Running the Project

1. Build the project:
```bash
dotnet build
```

2. Run the project:
```bash
dotnet run
```

## Next Steps

- [Code Samples](code_samples.md)
- [Advanced Topics](advanced_topics.md)
- [Contributing](CONTRIBUTING.md)