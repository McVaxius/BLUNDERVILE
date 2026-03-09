# Blundervile Plugin - Complete Project Plan

## Overview
**Plugin Name:** Blundervile  
**Purpose:** Convert the MGFFarming_McVaxius.lua script into a native C# Dalamud plugin for FFXIV  
**Primary Function:** Automate Gold Saucer MGF (Make it Rain) event farming  
**Future Scope:** Add whitelist management for group invites and address TODO items  

## Current Script Analysis

### Source Script: MGFFarming_McVaxius.lua
- **Location:** `D:\temp\dhogsbreakfeast\Gold Saucer\MGFFarming_McVaxius.lua`
- **Dependencies:** dfunc.lua library
- **Core Loop:** 
  1. Target "Blunderville Registrar" NPC
  2. Interact and navigate menus via callbacks
  3. Enter MGF instance (Territory 1165)
  4. Fail intentionally for 50 points per 4-minute run
  5. Return to Gold Saucer (Territory 1197)
  6. Repeat for specified count (default: 96 runs = 4800 points)

### Key Script Mechanics
- **Menu Navigation:** Uses `/callback` commands for dialog interactions
- **Territory Detection:** Monitors zone changes (1165 = fail area, 1197 = Gold Saucer)
- **State Tracking:** `in_saucer` flag prevents double-counting runs
- **Auto-shutdown:** Runs `/shutdown` after completion

### Dependencies Analysis: dfunc.lua
- **Utility Functions:** Navigation, targeting, zone transitions, inventory management
- **Key Functions Used:**
  - `TargetedInteract()` - Target and interact with NPCs
  - `ZoneTransition()` - Handle zone loading screens
  - `CharacterSafeWait()` - Wait for character availability
  - Configuration management via INI files

## Technical Architecture

### Plugin Structure
```
BLUNDERVILE/
├── Blundervile/
│   ├── Plugin.cs                 # Main plugin entry point
│   ├── Configuration.cs          # Plugin settings and config
│   ├── Models/
│   │   ├── MGFConfig.cs         # MGF-specific settings
│   │   └── PluginState.cs       # Runtime state tracking
│   ├── Services/
│   │   ├── MGFService.cs        # Core MGF automation logic
│   │   ├── NavigationService.cs # Movement and positioning
│   │   ├── DialogService.cs     # Menu/callback handling
│   │   └── TerritoryService.cs  # Zone change detection
│   ├── Windows/
│   │   ├── ConfigWindow.cs      # Plugin configuration UI
│   │   └── MainWindow.cs        # Status display window
│   ├── IPC/                     # Inter-plugin communication (future)
│   └── Blundervile.csproj       # Project file
├── Blundervile.sln              # Solution file
├── README.md                    # End-user documentation
├── CHANGELOG.md                 # Version history
└── .gitignore                   # Git ignore rules
```

### Core Components

#### 1. Plugin.cs (Main Entry)
- Plugin initialization and cleanup
- Service registration and dependency injection
- Command registration (`/blundervile`)
- Dalamud plugin lifecycle management

#### 2. MGFService.cs (Core Logic)
- **State Machine:** 
  - `Idle` → `TargetingRegistrar` → `NavigatingMenus` → `InMGF` → `Returning` → `Complete`
- **Run Counter:** Track completed runs vs target
- **Territory Monitoring:** Detect zone changes for run counting
- **Auto-shutdown:** Optional shutdown after completion

#### 3. DialogService.cs (Menu Navigation)
- **Callback Handler:** Replace `/callback` commands with AtkUnitBase.FireCallback
- **Addon Detection:** Wait for specific addons (FGSEnterDialog, ContentsFinderConfirm, etc.)
- **Yes/No Handling:** Auto-click confirmation dialogs
- **Menu State Tracking:** Prevent duplicate interactions

#### 4. NavigationService.cs (Movement)
- **NPC Targeting:** Find and target "Blunderville Registrar"
- **Position Tracking:** Monitor player movement for stuck detection
- **Short-range Navigation:** Use lockon+automove for NPC interaction
- **Fail-safe:** Timeout and retry logic

#### 5. TerritoryService.cs (Zone Detection)
- **Territory Type Monitoring:** Track current zone (1197, 1165)
- **Loading Screen Handling:** Safe zone transition detection
- **State Reset:** Clear state on zone changes
- **Run Counting:** Increment counter on successful return to Gold Saucer

## Implementation Phases

### Phase 1: Basic Plugin Infrastructure
**Objective:** Create minimal working plugin that can be loaded in-game

**Tasks:**
1. **Project Setup**
   - Create C# class library project
   - Add Dalamud.NET.Sdk package references
   - Configure build properties (Debug/Release)
   - Set up git repository and .gitignore

2. **Basic Plugin Structure**
   - Implement Plugin.cs with IDalamudPlugin interface
   - Add basic plugin metadata (name, version, author)
   - Set up dependency injection container
   - Register basic services

3. **Configuration System**
   - Create Configuration.cs with JSON serialization
   - Implement basic settings (enabled/disabled, run count)
   - Add config file management (save/load)
   - Create basic ConfigWindow.cs

4. **Testing Framework**
   - Verify plugin loads successfully
   - Test configuration persistence
   - Validate UI windows open correctly
   - Ensure clean plugin unload

**Deliverables:**
- Plugin loads in Dalamud without errors
- Basic configuration UI functional
- Settings persist between sessions
- Clean startup/shutdown behavior

**Testing Requirements:**
- Install plugin via `/pluginload` command
- Verify plugin appears in Dalamud plugin list
- Test configuration changes and reload
- Check for memory leaks on unload

---

### Phase 2: Core MGF Automation
**Objective:** Implement the basic MGF farming loop from the original script

**Tasks:**
1. **NPC Targeting System**
   - Implement "Blunderville Registrar" detection
   - Add targeting logic with retry mechanisms
   - Handle targeting failures and edge cases
   - Add distance checking and movement

2. **Dialog Navigation**
   - Map original `/callback` sequences to AtkUnitBase calls
   - Implement addon waiting logic
   - Handle FGSEnterDialog navigation
   - Add ContentsFinderConfirm handling

3. **Territory Detection**
   - Implement territory type monitoring
   - Add zone change event handling
   - Create run counting logic
   - Handle loading screen detection

4. **State Machine Implementation**
   - Create MGF automation states
   - Implement state transitions
   - Add timeout and error handling
   - Create status reporting system

**Key Callback Mappings:**
```csharp
// Original script callbacks → Plugin equivalents
"/callback FGSEnterDialog true 0"     → AtkUnitBase.FireCallback(true, 0)
"/callback FGSEnterDialog true -2"    → AtkUnitBase.FireCallback(true, -2)
"/callback ContentsFinderConfirm true 8" → AtkUnitBase.FireCallback(true, 8)
"/callback FGSSpectatorMenu true 3"   → AtkUnitBase.FireCallback(true, 3)
"/callback FGSExitDialog true 0"      → AtkUnitBase.FireCallback(true, 0)
```

**Deliverables:**
- Complete MGF automation loop
- Accurate run counting
- Stable territory detection
- Error recovery mechanisms

**Testing Requirements:**
- Stand in front of Blunderville Registrar
- Test complete automation cycle (1 run)
- Verify run counter increments correctly
- Test behavior with interruptions

---

### Phase 3: Enhanced Features & Polish
**Objective:** Add advanced features and improve reliability

**Tasks:**
1. **Whitelist System (Future)**
   - Design whitelist data structure
   - Add group invite detection
   - Implement auto-accept logic
   - Create whitelist management UI

2. **Advanced Navigation**
   - Add stuck detection and recovery
   - Implement alternative positioning
   - Add obstacle avoidance
   - Create path optimization

3. **Monitoring & Logging**
   - Add detailed logging system
   - Implement performance monitoring
   - Create statistics tracking
   - Add debug visualization

4. **Safety Features**
   - Add emergency stop functionality
   - Implement pause/resume capability
   - Add condition checking (combat, cutscenes)
   - Create backup state recovery

**Deliverables:**
- Robust error handling
- Comprehensive logging
- Performance optimization
- Safety mechanisms

**Testing Requirements:**
- Test with various interruptions
- Verify memory usage over time
- Test edge cases and error conditions
- Validate safety features work correctly

---

### Phase 4: Documentation & Release
**Objective:** Prepare for public release

**Tasks:**
1. **User Documentation**
   - Write comprehensive README.md
   - Create installation guide
   - Add troubleshooting section
   - Document configuration options

2. **Developer Documentation**
   - Comment code thoroughly
   - Create API documentation
   - Add contribution guidelines
   - Document architecture decisions

3. **Release Preparation**
   - Create release build configuration
   - Test on multiple systems
   - Verify compatibility
   - Prepare changelog

**Deliverables:**
- Complete user documentation
- Clean, commented code
- Tested release build
- Version 1.0.0 release

**Testing Requirements:**
- Fresh installation test
- Cross-platform compatibility
- Performance benchmarking
- User acceptance testing

## Technical Considerations

### Dalamud API Usage
- **Targeting:** Use `TargetManager` and `ObjectTable` for NPC detection
- **Dialogs:** Use `AtkUnitBase.FireCallback` for menu interactions
- **Territories:** Use `ClientState.TerritoryType` for zone detection
- **Conditions:** Use `ConditionFlag` for game state checking

### Memory Management
- **Event Unsubscription:** Clean up all event handlers in Dispose()
- **Service Disposal:** Implement IDisposable for all services
- **Weak References:** Use weak references for cached objects
- **Garbage Collection:** Monitor memory usage during long runs

### Thread Safety
- **UI Updates:** Dispatch UI updates to main thread
- **State Synchronization:** Use locks for shared state
- **Async Operations:** Properly handle async/await patterns
- **Plugin Communication:** Thread-safe IPC implementation

### Error Handling
- **Exception Logging:** Comprehensive error logging
- **Graceful Degradation:** Continue operation when possible
- **User Notifications:** Clear error messages to users
- **Recovery Mechanisms:** Automatic recovery from common errors

## Configuration Management

### Default Settings
```json
{
  "Enabled": false,
  "TargetRuns": 96,
  "AutoShutdown": true,
  "DebugMode": false,
  "RetryAttempts": 3,
  "InteractionDelay": 1000,
  "TerritoryTimeout": 30000
}
```

### User Preferences
- **Run Target:** Number of MGF runs to complete
- **Auto-shutdown:** Whether to shutdown PC after completion
- **Debug Mode:** Enable detailed logging
- **Interaction Speed:** Adjust timing for menu interactions
- **Safety Features:** Enable/disable various safety checks

## Testing Strategy

### Unit Testing
- **Service Logic:** Test individual service methods
- **State Machine:** Verify state transitions
- **Configuration:** Test settings persistence
- **Utility Functions:** Test helper methods

### Integration Testing
- **Plugin Lifecycle:** Test load/unload cycles
- **Service Interaction:** Test service communication
- **UI Integration:** Test UI functionality
- **Memory Management:** Test for leaks

### User Acceptance Testing
- **Complete Workflow:** Test end-to-end automation
- **Error Scenarios:** Test failure recovery
- **Performance:** Test long-running stability
- **Usability:** Test configuration UI

## Future Enhancements

### Whitelist System (Post-Release)
- **Group Invite Management:** Auto-accept from whitelisted players
- **Friend List Integration:** Sync with FFXIV friends
- **FC Member Support:** Auto-accept from FC members
- **Blacklist Support:** Block specific players

### Advanced Features
- **Multiple Character Support:** Different settings per character
- **Schedule System:** Run at specific times
- **Statistics Dashboard:** Track farming history
- **Cloud Sync:** Share settings across devices

### Integration Opportunities
- **Other Plugins:** IPC with popular plugins
- **Web Services:** Remote monitoring/control
- **Discord Integration:** Status notifications
- **Database Storage:** Advanced analytics

## Risk Assessment & Mitigation

### Technical Risks
- **Game Updates:** FFXIV patches may break callbacks
  - *Mitigation:* Version detection, fallback mechanisms
- **API Changes:** Dalamud API evolution
  - *Mitigation:* Minimal API usage, abstraction layers
- **Performance Issues:** Memory leaks, CPU usage
  - *Mitigation:* Regular profiling, optimization

### Usage Risks
- **Detection:** Automation detection by Square Enix
  - *Mitigation:* Human-like timing, randomization
- **Account Safety:** Plugin-related account issues
  - *Mitigation:* Clear warnings, user responsibility
- **Game Stability:** Plugin crashes affecting game
  - *Mitigation:* Exception handling, graceful failures

### Development Risks
- **Scope Creep:** Feature expansion beyond original goal
  - *Mitigation:* Clear phase boundaries, version planning
- **Technical Debt:** Rushed implementation choices
  - *Mitigation:* Code reviews, refactoring time
- **Dependencies:** Changes in required plugins
  - *Mitigation:* Minimal dependencies, alternative implementations

## Success Metrics

### Technical Metrics
- **Stability:** Zero crashes during 100+ test runs
- **Performance:** <1% CPU usage, <50MB memory
- **Reliability:** 99%+ successful automation completion
- **Response Time:** <100ms UI interaction latency

### User Metrics
- **Installation Success:** 100% successful first-time installs
- **Configuration Ease:** <5 minutes to configure
- **User Satisfaction:** Positive feedback and reviews
- **Bug Reports:** Minimal critical bug reports

## Conclusion

The Blundervile plugin represents a conversion of a proven Lua script into a modern C# Dalamud plugin. By following this phased approach, we ensure:

1. **Technical Excellence:** Clean, maintainable code architecture
2. **User Experience:** Intuitive interface and reliable automation
3. **Future Growth:** Extensible foundation for advanced features
4. **Quality Assurance:** Comprehensive testing and validation

The project leverages existing knowledge from similar plugins while addressing the specific requirements of MGF automation. The phased rollout allows for iterative improvement and user feedback integration.

**Next Steps:** Begin Phase 1 implementation with basic plugin infrastructure and validate the development environment is properly configured.
