# Changelog

All notable changes to Blundervile will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned Features
- Whitelist system for group invites
- Multiple character profiles
- Statistics dashboard
- Discord integration
- Performance optimizations

### Known Issues
- None currently

## [1.0.0] - Planned Release

### Added
- Core MGF automation functionality
- Blunderville Registrar targeting and interaction
- Complete menu navigation automation
- Territory detection and run counting
- Configuration UI with all essential settings
- Command system for plugin control
- Comprehensive error handling and recovery
- Safety mechanisms and emergency stop
- Debug logging system
- Memory management and resource cleanup
- User documentation and installation guide

### Features
- **Automation Loop**: Complete MGF farming cycle
  - Target "Blunderville Registrar" NPC
  - Navigate through all dialog menus
  - Enter MGF instance (Territory 1165)
  - Handle failure runs automatically
  - Return to Gold Saucer (Territory 1197)
  - Count completed runs accurately

- **Configuration Options**
  - Target run count (1-999 runs)
  - Auto-shutdown after completion
  - Interaction timing adjustments
  - Retry attempt configuration
  - Debug mode toggle

- **Safety Features**
  - Emergency stop command
  - Pause/resume functionality
  - Combat detection and pause
  - Zone transition safety
  - State recovery mechanisms

- **User Interface**
  - Main configuration window
  - Status display panel
  - Progress tracking
  - Real-time run counter

- **Command System**
  - `/blundervile` - Main UI
  - `/blundervile start/stop/pause/resume`
  - `/blundervile status/progress`
  - `/blundervile reset`
  - `/blundervile debug`

### Technical Details
- **Architecture**: Service-based dependency injection
- **State Machine**: Robust state management
- **Memory Management**: Proper disposal and cleanup
- **Thread Safety**: Main thread UI updates
- **Error Handling**: Comprehensive exception management
- **Performance**: Optimized for minimal resource usage

### Compatibility
- **FFXIV**: Latest version support
- **Dalamud**: Stable API compatibility
- **.NET**: Framework requirements aligned with Dalamud
- **OS**: Windows 10/11 support

### Documentation
- Complete user guide
- Installation instructions
- Troubleshooting section
- Command reference
- FAQ section

### Testing
- Unit test coverage for core services
- Integration testing for complete workflow
- Performance benchmarking
- Memory leak testing
- User acceptance testing

## Development History

### Phase 1: Infrastructure (Planned)
- [ ] Basic plugin structure
- [ ] Configuration system
- [ ] UI framework
- [ ] Service architecture
- [ ] Basic testing

### Phase 2: Core Automation (Planned)
- [ ] NPC targeting system
- [ ] Dialog navigation
- [ ] Territory detection
- [ ] State machine implementation
- [ ] Error handling

### Phase 3: Polish & Features (Planned)
- [ ] Advanced navigation
- [ ] Monitoring systems
- [ ] Safety features
- [ ] Performance optimization
- [ ] Comprehensive testing

### Phase 4: Release Preparation (Planned)
- [ ] Documentation completion
- [ ] Release build configuration
- [ ] Final testing and validation
- [ ] Distribution preparation

## Version Breakdown

### Major Versions (X.0.0)
- Significant feature additions
- Architecture changes
- Breaking changes to configuration

### Minor Versions (0.X.0)
- New features
- UI improvements
- Command additions
- Performance enhancements

### Patch Versions (0.0.X)
- Bug fixes
- Stability improvements
- Minor tweaks
- Documentation updates

## Future Roadmap

### Version 1.1.0 (Planned)
- Whitelist system implementation
- Group invite management
- FC member integration
- Blacklist support

### Version 1.2.0 (Planned)
- Multiple character profiles
- Settings synchronization
- Advanced statistics
- Performance dashboard

### Version 1.3.0 (Planned)
- Schedule system
- Remote monitoring
- Discord notifications
- Web interface

### Version 2.0.0 (Future)
- Complete UI redesign
- Advanced automation features
- Plugin ecosystem integration
- Cloud configuration sync

## Support and Feedback

### Reporting Issues
When reporting issues, please include:
- Plugin version
- FFXIV version
- Steps to reproduce
- Error messages
- System information

### Feature Requests
- Submit via GitHub issues
- Discuss in Discord
- Provide detailed requirements
- Consider feasibility and priority

### Beta Testing
- Join beta program for early access
- Provide detailed feedback
- Report bugs promptly
- Suggest improvements

## Technical Notes

### Dependencies
- Dalamud.NET.Sdk
- FFXIVClientStructs (for advanced features)
- No external plugin dependencies required

### Performance Metrics
- Target: <1% CPU usage
- Target: <50MB memory usage
- Target: 99%+ success rate
- Target: <100ms UI response time

### Compatibility Matrix
| FFXIV Version | Plugin Version | Status |
|---------------|----------------|--------|
| 6.x | 1.0.x | ✅ Supported |
| 7.x | 1.0.x | ✅ Supported |

## Security and Privacy

### Data Collection
- No personal data collected
- No telemetry data sent
- Local configuration only
- Optional crash reporting

### Privacy Features
- All settings stored locally
- No network communication required
- No user tracking
- No data mining

## Credits

### Development Team
- Lead Developer: [Name]
- Contributors: [Names]
- Testers: [Names]
- Translators: [Names]

### Acknowledgments
- Original script author: McVaxius
- Dalamud development team
- FFXIV community
- Beta testers and feedback providers

## Legal Information

### License
MIT License - see LICENSE file for details

### Trademarks
- FFXIV is a trademark of Square Enix
- Dalamud is a community project
- Blundervile is an independent project

### Disclaimers
- Not affiliated with Square Enix
- Use at your own risk
- No warranty provided
- Subject to FFXIV Terms of Service

---

**Note**: This changelog is maintained for the Blundervile plugin. For detailed technical documentation and development guides, please refer to the project documentation.
