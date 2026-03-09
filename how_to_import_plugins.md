# How to Import and Use Dalamud Plugins

## Prerequisites
- FFXIV installed and updated to latest version
- Dalamud installed and working
- Basic understanding of FFXIV interface

## Installation Methods

### Method 1: Automatic Installation (Recommended)
1. **Open FFXIV** and log into the game
2. **Open Dalamud Settings**:
   - Type `/xlsettings` in chat
   - Or click the Dalamud icon in your system tray
3. **Go to Plugin Installer** tab
4. **Add Custom Repository** (if not already added):
   - Click "Add Plugin Repository"
   - Enter repository URL when available
5. **Install Plugin**:
   - Find "Blundervile" in the plugin list
   - Click "Install"
   - Wait for installation to complete
6. **Enable Plugin**:
   - Go to "Installed Plugins" tab
   - Find "Blundervile" and click the toggle to enable

### Method 2: Manual Installation (Development)
1. **Download Plugin Files**:
   - Get the plugin files from the developer
   - Ensure you have the latest version

2. **Locate Dalamud Plugin Folder**:
   - Open Dalamud settings (`/xlsettings`)
   - Click "Open Plugin Directory" button
   - This opens the plugins folder

3. **Create Plugin Folder**:
   - In the plugins folder, create a new folder named `Blundervile`
   - Extract all plugin files into this folder

4. **Restart Dalamud**:
   - Close FFXIV completely
   - Relaunch FFXIV
   - Dalamud will automatically detect the new plugin

5. **Enable Plugin**:
   - Type `/plugins` in chat to open plugin list
   - Find "Blundervile" in the list
   - Click the checkbox to enable it

## First-Time Setup

### Basic Configuration
1. **Open Plugin UI**:
   - Type `/blundervile` in chat
   - Or find it in the Dalamud plugin list and click "Settings"

2. **Configure Basic Settings**:
   - Set your target number of MGF runs (default: 96)
   - Choose whether to auto-shutdown after completion
   - Adjust interaction timing if needed

3. **Position Character**:
   - Stand in front of the "Blunderville Registrar" NPC
   - Make sure you have a clear path to the NPC
   - Ensure you're not in combat or a cutscene

### Safety Precautions
- **Test First**: Start with a small number of runs (1-3) to test
- **Monitor**: Watch the first few runs to ensure everything works
- **Backup**: Save any important game data before long automation sessions
- **Supervision**: Don't leave unattended for extended periods initially

## Daily Usage

### Starting MGF Farming
1. **Position Yourself**:
   - Go to Gold Saucer (Teleport to Gold Saucer aetheryte)
   - Stand directly in front of "Blunderville Registrar"
   - Face the NPC directly

2. **Start Plugin**:
   - Type `/blundervile` to open the UI
   - Click "Start" button or use `/blundervile start`
   - Plugin will begin the automation process

3. **Monitor Progress**:
   - Watch the status window for current progress
   - Plugin will show runs completed vs target
   - Check for any error messages or warnings

### Stopping the Plugin
- **Manual Stop**: Click "Stop" in the UI or use `/blundervile stop`
- **Emergency Stop**: Type `/blundervile emergency` for immediate stop
- **Pause**: Use `/blundervile pause` to temporarily pause

### Troubleshooting Common Issues

#### Plugin Won't Load
- **Check Dalamud Version**: Ensure Dalamud is up to date
- **Verify Installation**: Make sure all files are in the correct folder
- **Check Dependencies**: Ensure required plugins are installed
- **Restart Game**: Sometimes a full restart is needed

#### Targeting Issues
- **Reposition Character**: Move closer to the NPC
- **Clear Obstructions**: Make sure nothing blocks the path
- **Check NPC Name**: Verify you're targeting "Blunderville Registrar"
- **Reset Position**: Move away and back to reset targeting

#### Menu Navigation Problems
- **Adjust Timing**: Increase interaction delay in settings
- **Check Addons**: Ensure required UI addons are enabled
- **Reset Interface**: Type `/uireload` to reset game UI
- **Restart Plugin**: Stop and restart the plugin

#### Counting Errors
- **Zone Detection**: Ensure territory changes are detected
- **Loading Screens**: Wait for complete zone loading
- **State Reset**: Use `/blundervile reset` to clear state
- **Verify Territory**: Check you're in the correct zones

## Advanced Configuration

### Settings Overview
```
Enabled:            Toggle plugin on/off
TargetRuns:         Number of runs to complete (1-999)
AutoShutdown:       Shutdown PC after completion (true/false)
DebugMode:          Enable detailed logging (true/false)
RetryAttempts:      Number of retry attempts (1-10)
InteractionDelay:   Delay between actions (500-5000ms)
TerritoryTimeout:   Zone change timeout (10000-60000ms)
```

### Performance Tuning
- **Faster Speed**: Reduce InteractionDelay (may cause errors)
- **Higher Reliability**: Increase InteractionDelay and RetryAttempts
- **Debug Mode**: Enable to see detailed operation logs
- **Memory Usage**: Monitor with `/xlstats` if concerned

### Safety Settings
- **Emergency Stop**: Always available via command
- **Pause on Combat**: Plugin pauses automatically in combat
- **Zone Validation**: Verifies correct territory before actions
- **State Recovery**: Automatic recovery from common errors

## Commands Reference

### Basic Commands
- `/blundervile` - Open plugin UI
- `/blundervile start` - Start automation
- `/blundervile stop` - Stop automation
- `/blundervile pause` - Pause current operation
- `/blundervile resume` - Resume paused operation
- `/blundervile reset` - Reset plugin state

### Status Commands
- `/blundervile status` - Show current status
- `/blundervile progress` - Show run progress
- `/blundervile config` - Show current configuration

### Debug Commands
- `/blundervile debug` - Toggle debug mode
- `/blundervile log` - Show recent log entries
- `/blundervile test` - Run basic functionality test

## Updates and Maintenance

### Updating Plugin
1. **Check for Updates**: Look for update notifications in Dalamud
2. **Backup Settings**: Export your current settings
3. **Install Update**: Use the plugin installer or manual method
4. **Restore Settings**: Import your saved settings
5. **Test Functionality**: Verify everything works after update

### Backup and Restore
1. **Export Settings**:
   - Open plugin settings
   - Click "Export" or "Backup" button
   - Save the configuration file

2. **Import Settings**:
   - Open plugin settings
   - Click "Import" or "Restore" button
   - Select your saved configuration file

### Clean Installation
If you experience persistent issues:
1. **Stop Plugin**: Ensure plugin is disabled
2. **Delete Folder**: Remove the Blundervile plugin folder
3. **Restart Game**: Close and restart FFXIV
4. **Fresh Install**: Follow installation steps again
5. **Configure Setup**: Set up your preferences again

## Support and Community

### Getting Help
- **Documentation**: Check this guide first
- **FAQ**: Look for frequently asked questions
- **Bug Reports**: Report issues with detailed information
- **Community**: Join the community Discord or forums

### Reporting Issues
When reporting problems, include:
- **Plugin Version**: Check which version you're using
- **FFXIV Version**: Note your game version
- **Error Messages**: Copy any error text exactly
- **Steps to Reproduce**: Describe what leads to the issue
- **System Info**: Your OS and basic system specs

### Feature Requests
- **Forum**: Post suggestions in the appropriate forum
- **Discord**: Discuss ideas with the community
- **GitHub**: Create enhancement requests on the project page

## Best Practices

### Daily Usage
- **Start Small**: Test with few runs before long sessions
- **Monitor Initially**: Watch the plugin work the first few times
- **Regular Breaks**: Don't run continuously for extremely long periods
- **Keep Updated**: Maintain current plugin and Dalamud versions

### Safety Guidelines
- **Supervision**: Don't leave completely unattended initially
- **Backup Data**: Save important game progress
- **Account Safety**: Understand automation risks
- **Terms of Service**: Be aware of FFXIV ToS regarding automation

### Performance Optimization
- **Close Unused Apps**: Reduce background applications
- **Check Network**: Ensure stable internet connection
- **Monitor Resources**: Watch CPU and memory usage
- **Regular Restarts**: Restart game periodically for stability

## FAQ

### Q: Can I get banned for using this plugin?
A: While the plugin is designed to be safe, any automation carries some risk. Use responsibly and at your own discretion.

### Q: Why isn't the plugin finding the NPC?
A: Ensure you're standing directly in front of "Blunderville Registrar" in Gold Saucer. Try moving closer or resetting your position.

### Q: The plugin stopped working after an FFXIV update.
A: Game updates can break plugins. Wait for a plugin update that supports the new game version.

### Q: Can I use this on multiple characters?
A: Yes, settings are saved per character by default.

### Q: How many runs can I do safely?
A: The default of 96 runs (4800 points) is generally considered safe. Use your judgment and don't be excessive.

### Q: The run counter seems incorrect.
A: Territory detection issues can affect counting. Try the reset command and ensure stable zone transitions.

### Q: Can I customize the interaction speed?
A: Yes, adjust the InteractionDelay setting in the configuration menu.

### Q: Is there a mobile app or remote control?
A: Currently not, but this may be considered for future versions.

### Q: How do I uninstall the plugin?
A: Disable it in Dalamud, then delete the Blundervile plugin folder.

### Q: The plugin consumes too much CPU/memory.
A: This is unusual; try restarting the game or checking for memory leaks in the debug log.

## Conclusion

This plugin is designed to make MGF farming more convenient while maintaining safety and reliability. Always monitor the plugin initially and use it responsibly. If you encounter issues, refer to this guide or seek help from the community.

Remember that automation should enhance your gaming experience, not replace it entirely. Use the plugin as a tool to reduce tedious repetition while still engaging with the game content.
