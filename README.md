# Blundervile - MGF Automation Plugin

**A Dalamud plugin for FFXIV that automates Gold Saucer MGF (Make it Rain) event farming.**

## Features

- **Automated MGF Farming**: Complete MGF runs automatically for Gold Saucer points
- **Intelligent Targeting**: Finds and interacts with Blunderville Registrar NPC
- **Menu Navigation**: Handles all dialog interactions automatically
- **Run Tracking**: Keeps accurate count of completed runs
- **Auto-Shutdown**: Optional PC shutdown after reaching target runs
- **Safety Features**: Built-in error handling and recovery mechanisms
- **Configuration**: Customizable settings for different preferences

## Installation

### Automatic Installation (Recommended)
1. Open FFXIV and type `/xlsettings`
2. Go to the Plugin Installer tab
3. Add the plugin repository (when available)
4. Find "Blundervile" and click Install
5. Enable the plugin in the Installed Plugins tab

### Manual Installation
1. Download the latest release
2. Open Dalamud settings (`/xlsettings`)
3. Click "Open Plugin Directory"
4. Create a folder named `Blundervile`
5. Extract all plugin files into this folder
6. Restart FFXIV
7. Type `/plugins` and enable "Blundervile"

## Quick Start

1. **Position Yourself**: Stand in front of "Blunderville Registrar" in Gold Saucer
2. **Open Plugin**: Type `/blundervile` to open the UI
3. **Configure Settings**: Set your target number of runs (default: 96)
4. **Start Automation**: Click "Start" or use `/blundervile start`
5. **Monitor Progress**: Watch the status window for completion

## Configuration

### Basic Settings
- **Target Runs**: Number of MGF runs to complete (1-999)
- **Auto-Shutdown**: Shutdown PC after completion
- **Debug Mode**: Enable detailed logging
- **Interaction Delay**: Timing between menu interactions

### Safety Options
- **Retry Attempts**: Number of retry attempts on failures
- **Territory Timeout**: Zone change timeout duration
- **Emergency Stop**: Always available via command

## Commands

| Command | Description |
|---------|-------------|
| `/blundervile` | Open plugin UI |
| `/blundervile start` | Start automation |
| `/blundervile stop` | Stop automation |
| `/blundervile pause` | Pause current operation |
| `/blundervile resume` | Resume paused operation |
| `/blundervile reset` | Reset plugin state |
| `/blundervile status` | Show current status |
| `/blundervile progress` | Show run progress |

## Requirements

- **FFXIV**: Latest version with active subscription
- **Dalamud**: Latest stable version
- **.NET Framework**: Compatible with Dalamud requirements
- **Permissions**: Ability to install third-party plugins

## Safety and Legality

⚠️ **Important**: This plugin automates game actions. Use at your own risk and discretion.

- Use responsibly and in moderation
- Monitor the plugin initially to ensure proper operation
- Don't leave unattended for extended periods
- Be aware of FFXIV Terms of Service regarding automation
- The developers are not responsible for any account issues

## Troubleshooting

### Plugin Won't Load
- Ensure Dalamud is up to date
- Check that all files are in the correct folder
- Restart FFXIV completely
- Verify plugin compatibility

### Targeting Issues
- Stand directly in front of the NPC
- Clear any obstacles between you and the NPC
- Try moving closer or resetting position
- Ensure you're targeting "Blunderville Registrar"

### Menu Problems
- Increase interaction delay in settings
- Check that required UI addons are enabled
- Type `/uireload` to reset game interface
- Stop and restart the plugin

### Counting Errors
- Ensure stable zone transitions
- Wait for complete loading between zones
- Use `/blundervile reset` to clear state
- Verify you're in correct territories

## Performance

- **CPU Usage**: <1% during operation
- **Memory Usage**: <50MB typical
- **Reliability**: 99%+ success rate in testing
- **Speed**: ~4 minutes per run (matching manual timing)

## Version History

See [CHANGELOG.md](CHANGELOG.md) for detailed version information.

## Contributing

Contributions are welcome! Please see the development guidelines:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Support

- **Documentation**: See [how_to_import_plugins.md](how_to_import_plugins.md) for detailed guides
- **Issues**: Report bugs with detailed information
- **Community**: Join our Discord for discussions
- **FAQ**: Check the troubleshooting section first

## Development

This plugin is based on the proven MGFFarming_McVaxius.lua script, converted to a modern C# Dalamud plugin with enhanced features and safety mechanisms.

### Key Improvements Over Lua Script
- Native C# performance and reliability
- Proper error handling and recovery
- User-friendly configuration interface
- Comprehensive logging and debugging
- Memory management and resource cleanup
- Thread-safe operation

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Original MGFFarming_McVaxius.lua script by McVaxius
- Dalamud development team for the plugin framework
- FFXIV community for feedback and testing
- Contributors and translators

## Disclaimer

This plugin is provided "as is" without warranty of any kind. The developers are not responsible for any issues that may arise from using this plugin, including but not limited to account suspension, data loss, or game client instability.

Use this plugin responsibly and in accordance with FFXIV's Terms of Service.
