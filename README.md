# Azure IoT Telemetry Monitoring Web Application

A web-based dashboard for monitoring telemetry received through Azure IoT and processed using Node-RED. The React frontend displays the latest available telemetry information in a clear and organized interface.

## Overview

The **Azure IoT Telemetry Monitoring Web Application** demonstrates how IoT telemetry can be received, processed, and presented through a web dashboard. The application connects a React frontend to a Node-RED HTTP endpoint to retrieve the latest telemetry data.

The dashboard is designed to display connection status, received ASCII values, the converted message, and the timestamp associated with the available data.

## Features

- **Telemetry dashboard:** Displays the latest telemetry data returned by the backend.
- **Connection status:** Shows the connection status provided by the backend.
- **ASCII values:** Displays received ASCII values when available.
- **Converted message:** Presents the converted telemetry string.
- **Timestamp:** Shows the timestamp included in the backend response.
- **Automatic refresh:** Periodically requests updated data from the backend.
- **Responsive interface:** Provides a web interface built using React.

> Note: The displayed information depends on the data received and returned by the Node-RED flow.

## Technology Stack

| Component | Technology |
|---|---|
| Frontend | React.js |
| Backend and flow processing | Node-RED |
| IoT telemetry source | Azure IoT |
| API communication | HTTP and JSON |
| Development tools | Node.js, npm, Git |

## System Architecture

```text
IoT Device / Telemetry Source
              |
              v
        Azure IoT Hub
              |
              v
          Node-RED
    Receive and process data
              |
              v
       HTTP /data endpoint
              |
              v
        React Frontend
              |
              v
       Telemetry Dashboard
```

The diagram represents the intended data flow. The actual telemetry source and Azure-to-Node-RED connection depend on the configured IoT flow.

## Project Structure

```text
azure-iot-telemetry-monitoring/
├── public/
│   ├── index.html
│   ├── manifest.json
│   └── ...
├── src/
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   ├── index.css
│   └── ...
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

- `public/` contains the static files used by the React application.
- `src/App.js` contains the main dashboard component.
- `src/App.css` contains dashboard-specific styling.
- `src/index.js` initializes the React application.
- `src/index.css` contains global styles.
- `package.json` defines the frontend dependencies and scripts.
- `README.md` documents the project and setup instructions.

## Prerequisites

Install the following before running the project:

- Node.js and npm
- Git
- A web browser
- Node-RED with the project's configured telemetry flow
- Access to the configured Azure IoT telemetry source, if required

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/pranathiv29/azure-iot-telemetry-monitoring.git
cd azure-iot-telemetry-monitoring
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the React application

On Windows PowerShell, use:

```powershell
npm.cmd start
```

On terminals where `npm` works normally, use:

```bash
npm start
```

The application should open at:

http://localhost:3000

### 4. Start Node-RED

Start Node-RED using your local installation. For the Windows setup used during development:

```powershell
node-red.cmd
```

Open the Node-RED editor at:

http://127.0.0.1:1880/

Import or configure the project's Node-RED flow and the required Azure IoT connection using your authorized credentials.

### 5. Verify the backend endpoint

The React dashboard is configured to request data from:

```text
http://127.0.0.1:1880/data
```

Open the endpoint in your browser to check whether it returns JSON.

The dashboard requires the backend to return the expected fields, including the received ASCII values, converted string, timestamp, and connection status.

If the endpoint is unavailable, verify that Node-RED is running and that the HTTP endpoint is configured correctly.

## Example Data Format

The following is an illustrative JSON response showing the expected field structure. It is not a record of actual telemetry:

```json
{
  "receivedAsciiValues": [111, 110, 101],
  "convertedString": "one",
  "timestamp": "2026-10-22T03:45:21.727Z",
  "connectionStatus": "Connected"
}
```

The actual values depend on the telemetry received by Node-RED.

## Configuration

The frontend and backend must use compatible endpoint settings.

If the Node-RED endpoint or port changes, update the corresponding API URL in the React application.

For a deployment on another computer, replace the local loopback address with the appropriate backend address and configure network access as required.

**Security:** Never commit Azure IoT connection strings, SharedAccessKey values, passwords, access tokens, or other secrets. Keep credentials in an appropriate local configuration or secret-management system.

## Troubleshooting

| Problem | What to check |
|---|---|
| React application does not start | Check Node.js, npm, and dependency installation. |
| Dashboard cannot retrieve data | Confirm that Node-RED is running and the `/data` endpoint is available. |
| No telemetry is displayed | Check whether new telemetry reaches the Node-RED flow. |
| Connection status shows waiting or disconnected | Check the backend flow and its connection-status logic. |
| Browser reports a network or CORS error | Verify the endpoint URL and backend CORS configuration. |
| Data disappears after restarting Node-RED | Check whether the flow stores the latest message only in memory. |

## Current Scope and Limitations

- The dashboard displays the latest data made available by the backend.
- Data availability depends on the configured telemetry source and Node-RED flow.
- The current API uses a local Node-RED address during development.
- Public deployment and remote-device access require additional configuration.
- Historical analytics, authentication, persistent storage, and alerting should be treated as future enhancements unless separately implemented.

## Future Enhancements

- Add historical telemetry charts and data logging.
- Introduce configurable API endpoints.
- Add device-wise monitoring and filtering.
- Implement alerts for selected telemetry conditions.
- Deploy the frontend and backend to an accessible hosting environment.
- Add authentication and secure remote access.

## Author

**Pranathi V**

GitHub: [@pranathiv29](https://github.com/pranathiv29)

## License

No license has been specified yet. Contact the repository owner for permission before reusing or redistributing this project.
