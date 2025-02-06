# Bootstrap Command
- If there is no `.windsurfrules` file, or when the agent receives the `bootstrap` command, it will:
  - Preserve any extra keywords (e.g., "tutorial") and pass them along as context.
  - Trigger the general bootstrap process
- Follow global rules if no specific rule applies.

## Cross-Platform Considerations
- Use PowerShell for terminal commands on Windows.
- Use Bash for terminal commands on macOS/Linux.

## Bootstrap Process
- Verifies and, if necessary, updates the `.windsurfrules` file by checking [https://github.com/ZarK/ai-rules](https://github.com/ZarK/ai-rules).
- Creates a corresponding `.cursorrules` file for compatibility with Cursor.
- Start the "General Bootstrap" process as defined in the `.windsurfrules`, passing along any context keywords.
