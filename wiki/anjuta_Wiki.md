# SigmaOS-anjuta Component Wiki

## Overview
SigmaOS-anjuta provides Anjuta IDE support and IDE integration for the SigmaOS operating system. It demonstrates the IDE subsystem and Anjuta integration within the SigmaOS ecosystem, following the principles of clear abstraction and deterministic IDE initialization.

## Principles
- Single Responsibility
- IDE Abstraction
- Fail-Fast on IDE Initialization Errors
- Deterministic IDE Setup
- Clear Abstraction Over IDE APIs
- Composition over Inheritance for IDE extensions

## Architecture
SigmaOS-anjuta follows an IDE pattern:
- **IDE Core**: Provides Anjuta IDE support, IDE integration, and IDE lifecycle
- **IDE Integration**: Supports Anjuta IDE, IDE features, and IDE plugin management
- **IDE Lifecycle**: Supports IDE startup, IDE shutdown, and IDE session management
- **Error Handling**: Fail-fast on invalid IDE configurations or unsupported IDE types

## API
The component provides the following public APIs:
- `ide::anjuta::launch()` - Launch Anjuta IDE
- `ide::project::open(project_path)` - Open an Anjuta project
- `ide::plugin::manage(plugin)` - Manage Anjuta plugin
- `ide::status::ide()` - Get IDE status and IDE availability
- Error types for IDE failure scenarios or unsupported IDE types

## Test Structure (Arrange-Act-ASSERT)
All tests follow the AAA pattern:
1. **Arrange**: Set up test environment with specific IDE configuration
2. **Act**: Execute the code under test (IDE launch, project opening)
3. **Assert**: Verify the expected IDE results

Example:
```rust
#[test]
fn test_ide_launch_aaa() {
    // Arrange
    
    // Act
    let result = ide::anjuta::launch();
    
    // Assert
    assert!(result.is_ok());
    let launched = result.unwrap();
    assert!(launched.is_running());
}
```

## Development
- Follows Rust best practices with `#![forbid(unsafe_code)]`
- IDE initialization is best-effort; gracefully degrades on unsupported configurations
- Comprehensive error types for all IDE failure scenarios
- Unit tests provided for IDE launch and project opening
- Integration tests for full IDE system with actual IDE integration

## TODO
- Add support for additional IDE types (VS Code, Eclipse, IntelliJ)
- Expand IDE capabilities (IDE features, IDE plugins, IDE customization)
- Add lifecycle features (IDE startup, IDE shutdown, IDE session management)
- Create integration tests with actual IDE systems and IDE integration
- Implement IDE persistence and IDE state management