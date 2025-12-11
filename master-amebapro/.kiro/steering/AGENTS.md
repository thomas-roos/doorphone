# Agent Guidelines for Doorbell Project

## Project Context
- AmebaProII-based video doorbell using FreeRTOS WebRTC
- AWS IoT integration with KVS streaming
- Embedded C development with ARM GCC toolchain

## Code Standards
- Minimal, focused implementations
- Follow existing FreeRTOS patterns
- Use existing project structure and naming conventions
- Prioritize embedded system constraints (memory, performance)

## Development Workflow
- Always show plan before making code changes
- Save planning documents before executing for repeatability (in `.kiro/plans/` directory)
- Always show code changes and ask for permission before executing
- Stage current changes with `git add .` before ANY code modifications
- NEVER push anything - all pushes must be done manually
- Read existing code structure before modifications
- Test build compatibility with existing toolchain
- Maintain compatibility with setup script automation

## File Organization
- Keep doorbell-specific code in separate files
- Use `doorbell_config.h` for configuration
- Follow existing include patterns in `master.c`

## Communication Style
- Direct, technical responses
- Focus on actionable solutions
- Explain embedded-specific considerations
- Reference hardware constraints when relevant
