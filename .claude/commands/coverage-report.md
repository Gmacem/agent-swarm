# Coverage Report

Run test coverage analysis and identify gaps.

## Arguments

- `$ARGUMENTS` — Optional: specific directory or module to analyze

## Instructions

1. Check `prompts/project.md` for the coverage tool and config.
2. Run the coverage tool on the specified target (or the whole project).
3. Report:
   - Overall coverage percentage.
   - Per-file coverage breakdown.
   - Uncovered lines and functions.
   - Files with no test coverage at all.
4. Identify the highest-impact coverage gaps — critical code paths without tests.
5. Suggest which tests to write next for maximum coverage improvement.
6. Update your task with the results.
