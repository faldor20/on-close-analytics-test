# on-close-analytics-test

A static site to test on-close analytics effectiveness across different browser events and sending methods.

## 🚀 Features

- **Multiple Event Listeners**: Tests analytics on various browser events:
  - `beforeunload` - Page close or reload
  - `pagehide` - More reliable alternative to beforeunload
  - `visibilitychange` - Tab switch or minimize
  - `freeze` - Page Lifecycle API freeze event
  - `resume` - Page becomes active again
  - `unload` - Legacy unload event

- **Flexible Sending Methods**:
  - `navigator.sendBeacon()` - Recommended for page unload
  - `fetch()` with `keepalive: true` - Alternative approach

- **Configurable Endpoint**: Send events to any webhook endpoint (e.g., webhook.site)

- **URL-based Configuration**: Settings saved in URL parameters for easy sharing

- **Real-time Event Log**: See all events and analytics sends in real-time

## 📖 Usage

1. Open `index.html` in your browser
2. Get a webhook URL from [webhook.site](https://webhook.site) or any similar service
3. Enter the webhook URL in the configuration section
4. Choose between sendBeacon or fetch with keepalive
5. Click "Save Configuration" - settings will be saved in the URL
6. Test different scenarios:
   - Click "Manual Test Send" to send immediately
   - Switch tabs to trigger visibilitychange
   - Close the tab to trigger beforeunload/pagehide
   - Navigate away to test navigation events

## 🔗 Sharing

The configuration is saved in URL parameters, so you can share the configured page:
```
index.html?endpoint=https://webhook.site/your-id&method=beacon
```

## 🧪 What Gets Sent

Each analytics event includes:
- `event` - Event type (beforeunload, pagehide, etc.)
- `sendingMethod` - Method used to send the event (beacon/fetch)
- `deviceType` - Type of device (mobile/tablet/desktop)
- `browser` - Browser name (Chrome, Firefox, Safari, Edge, etc.)
- `userAgent` - Full browser user agent string
- `timestamp` - ISO 8601 timestamp
- `url` - Current page URL
- Additional event-specific data

## 🌐 Deployment

This is a static site consisting of a single HTML file. Deploy to:
- GitHub Pages
- Netlify
- Vercel
- Any static hosting service
- Or just open the file locally

## 🎯 Testing Best Practices

- Test in multiple browsers (Chrome, Firefox, Safari, Edge)
- Try on mobile devices
- Test both desktop and mobile scenarios
- Compare sendBeacon vs fetch with keepalive reliability
- Monitor your webhook endpoint to see which events successfully deliver
