## Code Generation Instructions
- Always include comments in the provided code.
- Prefer using `async/await/task` over traditional promises.
- Task should be used for CPU-bound operations.
- Always prefer multithreading for I/O-bound operations.
- Use `using` statements for disposable objects.
- Always implement memory efficient code.
- Use `StringBuilder` for string concatenation.
- Use `IEnumerable` for collections.
- Do not use var for any variable declaration.
- Use `readonly` for immutable fields.
- Always use `try-catch` blocks for error handling.
- Always ensure no variable is null before using it.
- Use `string.IsNullOrEmpty` for string checks.
- Always use a complete code example with extensive comments.
- Use descriptive variable names.
- Avoid using global variables.
- Always surround code with `// code-start-csharp` and `// code-end-csharp`, replace csharp with for example bash or hlsl depending on the language used in the code block.
- Always include comments in detail which walk the user through the code provided.

## Review Selection Instructions
- Highlight any potential performance issues.
- Suggest improvements for code readability.
- Check for adherence to coding standards.
- Identify any missing edge case handling.
- Review the use of third-party libraries for necessity.

## Commit Message Generation Instructions
- Provide a detailed description of the changes in the body.
- Mention any related issue numbers.
- Use bullet points for multiple changes.
