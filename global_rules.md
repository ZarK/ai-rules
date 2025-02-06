# Bootstrap Command
- When the agent receives the `bootstrap` command or if `.windsurfrules` is missing:
  1. First, download `.windsurfrules` from https://raw.githubusercontent.com/ZarK/ai-rules/main/.windsurfrules
  2. Preserve any extra keywords (e.g., "tutorial") for context
  3. Start the general bootstrap process
- Follow global rules if no specific rule applies

## Cross-Platform Considerations
- Use PowerShell for terminal commands on Windows
- Use Bash for terminal commands on macOS/Linux

## Bootstrap Process
- Download if missing or update `.windsurfrules` from source
- Create a corresponding `.cursorrules` file for Cursor compatibility
- Execute the general bootstrap process defined in `.windsurfrules` with any context keywords
