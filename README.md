# EdgeFlow Frontend

A real-time industrial monitoring dashboard built with React, TypeScript, and WebSocket connectivity. EdgeFlow provides live visualization of industrial sensor data including coolant temperature, vibration levels, hydraulic pressure, and system status.

## Features

- **Real-time Data Streaming**: WebSocket connection using STOMP protocol for live sensor data
- **Industrial Dashboard**: Clean, modern interface displaying critical system metrics
- **Responsive Design**: Material-UI components with custom styling
- **Auto-reconnection**: Robust WebSocket connection with automatic reconnection
- **TypeScript**: Full type safety throughout the application

## Tech Stack

- **Frontend**: React 19, TypeScript
- **UI Library**: Material-UI (MUI) v7
- **WebSocket**: STOMP.js with SockJS fallback
- **Build Tool**: Vite
- **Styling**: CSS Modules with custom properties

## Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- A WebSocket server endpoint providing STOMP protocol data

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd edgeflow-fe
```

2. Install dependencies:
```bash
npm install
```

3. Configure environment variables:
Create a `.env` file in the root directory:
```env
VITE_WS_URL=ws://your-websocket-server:port/ws
```

4. Start the development server:
```bash
npm run dev
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Project Structure

```
src/
├── components/
│   ├── Dashboard.tsx          # Main dashboard component
│   ├── Dashboard.module.css   # Dashboard styles
│   ├── StatusIndicator.tsx    # (Future component)
│   └── SensorCard.tsx         # (Future component)
├── utils/
│   └── stompClient.ts         # WebSocket/STOMP client logic
├── assets/                    # Static assets
├── App.tsx                    # Main application component
└── App.module.css            # Global styles and CSS variables
```

## WebSocket Data Format

The application expects WebSocket messages on `/topic/data` with the following JSON structure:

```json
{
  "coolantTemp": "75.2",
  "vibrationLevel": "2.1",
  "hydraulicPressure": "145.8",
  "systemStatus": "OPERATIONAL",
  "timestamp": "2024-01-15T10:30:00Z"
}
```

## Configuration

### Environment Variables

- `VITE_WS_URL`: WebSocket server URL (required)

### Styling

The application uses CSS custom properties for theming:

```css
:root {
  --brand-green: #05b8b1;
  --brand-blue: #005677;
  --primary-text: #495a66;
  --card-bg: #343131;
  --white: #ffffff;
}
```

## WebSocket Connection

The STOMP client automatically:
- Connects to the configured WebSocket endpoint
- Subscribes to `/topic/data` for sensor updates
- Handles reconnection with 3-second delay
- Logs connection status and errors

## Development

### Adding New Components

1. Create component in `src/components/`
2. Add corresponding CSS module if needed
3. Export from component file
4. Import and use in parent components

### Modifying Data Display

Update the `Dashboard.tsx` component to add new sensor readings or modify the display format.

## Production Build

```bash
npm run build
```

The build artifacts will be stored in the `dist/` directory.

## Browser Support

- Modern browsers with WebSocket support
- ES2015+ features required

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run linting: `npm run lint`
5. Submit a pull request

## License

See LICENSE file for details.

## Troubleshooting

### WebSocket Connection Issues

1. Verify `VITE_WS_URL` is correctly set
2. Check that the WebSocket server is running
3. Ensure the server supports STOMP protocol
4. Check browser console for connection errors

### Build Issues

1. Clear node_modules and reinstall: `rm -rf node_modules package-lock.json && npm install`
2. Check TypeScript errors: `npx tsc --noEmit`
3. Verify all dependencies are compatible