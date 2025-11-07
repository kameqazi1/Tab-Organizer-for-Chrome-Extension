# Tab Organizer

A Chrome extension that uses AI to intelligently organize your browser tabs into logical groups based on content, context, and usage patterns. Powered by Anthropic's Claude API.

## Description

Tab Organizer helps you manage browser tab clutter by automatically analyzing your open tabs and suggesting smart groupings. Whether you're researching a topic, working on multiple projects, or browsing for entertainment, Tab Organizer identifies patterns and creates organized tab groups that make sense.

The extension uses advanced AI to understand the context and relationships between your tabs, then suggests color-coded groups that you can apply with a single click. It also tracks your browsing patterns over time to provide increasingly accurate suggestions.

## Features

- 🤖 **AI-Powered Analysis**: Uses Anthropic's Claude API to intelligently analyze tab content and suggest logical groupings
- 🎨 **Color-Coded Groups**: Automatically suggests appropriate colors for each tab group
- 📊 **Smart Context Detection**: Identifies related tabs based on topics, domains, and usage patterns
- ⚡ **One-Click Organization**: Apply suggested groupings instantly with a single click
- 📈 **Usage Tracking**: Monitors time spent on tabs and scroll depth to improve suggestions
- 🔄 **Automatic Analysis**: Periodically analyzes your tabs in the background (every 30 minutes)
- 🎯 **Confidence Scores**: Shows how confident the AI is about each suggested grouping
- 🔒 **Privacy-Focused**: All API calls are made securely through the extension's service worker

## Installation

### From Source

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd tab-organizer
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the extension:
   ```bash
   npm run build
   ```

4. Load the extension in Chrome:
   - Open Chrome and navigate to `chrome://extensions/`
   - Enable "Developer mode" (toggle in the top right)
   - Click "Load unpacked"
   - Select the `dist` folder from this project

## Setup

### Getting Your Anthropic API Key

1. Visit [Anthropic Console](https://console.anthropic.com)
2. Sign up or log in to your account
3. Navigate to API Keys section
4. Create a new API key (it should start with `sk-ant-`)
5. **Important**: Make sure you have credits in your Anthropic account. You can add credits in the [Billing section](https://console.anthropic.com/settings/billing)

### Configuring the Extension

1. Click the Tab Organizer icon in your Chrome toolbar
2. Click the Settings icon (⚙️) in the top right
3. Paste your Anthropic API key in the input field
4. Click "Save"

## Usage

### Manual Analysis

1. Open multiple tabs (at least 3) that you want to organize
2. Click the Tab Organizer extension icon
3. Click "Analyze Tabs Now"
4. Review the suggested groups with their confidence scores
5. Click the checkmark (✓) to apply a grouping, or the X to dismiss it

### Automatic Analysis

The extension automatically analyzes your tabs every 30 minutes and shows a badge on the extension icon with the number of new suggestions.

### Applying Groups

- **Apply**: Click the green checkmark button to create the tab group
- **Dismiss**: Click the red X button to remove the suggestion

## Technical Details

### Architecture

- **Frontend**: React 19 + TypeScript
- **Styling**: Tailwind CSS
- **Build Tool**: Vite with @crxjs/vite-plugin
- **Icons**: Lucide React
- **AI Service**: Anthropic Claude API (claude-3-5-sonnet-20241022)

### Project Structure

```
tab-organizer/
├── src/
│   ├── background/          # Service worker for background tasks
│   ├── content/             # Content scripts for tab tracking
│   ├── popup/               # Extension popup UI
│   ├── utils/               # Core utilities
│   │   ├── aiService.ts      # Anthropic API integration
│   │   ├── storage.ts        # Chrome storage utilities
│   │   └── tabAnalyzer.*    # Tab analysis logic
│   └── types/               # TypeScript type definitions
├── public/                  # Static assets (icons)
└── dist/                    # Built extension (generated)
```

### Permissions

The extension requires the following permissions:
- `tabs`: To read and organize your tabs
- `tabGroups`: To create and manage tab groups
- `storage`: To save your API key and preferences
- `alarms`: For periodic background analysis
- `history`: To understand browsing patterns
- `scripting`: To inject content scripts

## Development

### Prerequisites

- Node.js 18+ and npm
- Chrome browser for testing

### Development Commands

```bash
# Install dependencies
npm install

# Run development server (with hot reload)
npm run dev

# Build for production
npm run build

# Lint code
npm run lint

# Preview production build
npm run preview
```

### Development Workflow

1. Make changes to the source files in `src/`
2. Run `npm run build` to compile
3. Reload the extension in `chrome://extensions/`
4. Test your changes

## Troubleshooting

### "API key not found" error
- Make sure you've saved your API key in Settings
- Verify the key starts with `sk-ant-`

### "Credit balance too low" error
- Add credits to your Anthropic account at [console.anthropic.com/settings/billing](https://console.anthropic.com/settings/billing)

### "No suggestions" message
- Ensure you have at least 3 tabs open
- Check that your tabs are not all Chrome internal pages (chrome://)
- Verify your API key is valid and has credits

### Extension not working
- Reload the extension in `chrome://extensions/`
- Check the browser console for errors (right-click extension icon → Inspect)
- Verify all permissions are granted

## Privacy & Security

- Your API key is stored locally in Chrome's storage and never shared
- Tab data is only sent to Anthropic's API for analysis
- No browsing data is stored permanently without your consent
- All API communications are encrypted via HTTPS

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.

## Support

For issues, questions, or feature requests, please open an issue on the GitHub repository.

---

**Note**: This extension requires an Anthropic API key with sufficient credits to function. The AI analysis uses Anthropic's Claude API, which may incur costs based on usage.
