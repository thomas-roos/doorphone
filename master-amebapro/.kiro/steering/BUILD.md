# Build Steering Rule

## Context Management
When building projects, capture stdout to file and analyze afterwards to prevent context overflow.

## Implementation
Use `build_and_analyze.sh` script that:
- Captures all build output to `build_output.txt`
- Provides concise analysis with exit code, file sizes, warning/error counts
- Shows only last few lines for success or last 20 lines for failures
- Preserves full log for detailed inspection when needed

## Usage
```bash
./build_and_analyze.sh
```

## Benefits
- Prevents context overflow from verbose build output
- Maintains build history in log files
- Provides actionable summary information
- Enables efficient troubleshooting when builds fail
