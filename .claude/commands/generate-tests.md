# Generate Tests

Generate tests for specified code.

## Arguments

- `$ARGUMENTS` — File path or function name to generate tests for

## Instructions

1. Read the target code and understand its behavior.
2. Check `prompts/project.md` for the test framework and conventions.
3. Generate tests covering:
   - **Happy path:** Normal expected inputs and outputs.
   - **Edge cases:** Boundary values, empty inputs, max values.
   - **Error cases:** Invalid inputs, missing data, failure scenarios.
   - **Integration points:** If the code calls external services or databases.
4. Write tests following the project's testing conventions.
5. Run the tests to verify they pass.
6. Report what was generated and the coverage achieved.
