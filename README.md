# EcoCharge Wi-Fi Web App

## What changed
- Battery health is visible on the main Dashboard even before connection.
- Top-right Connect now connects to a real EcoCharge ESP32 over the local Wi-Fi network.
- The browser checks `http://<ESP32-IP>/api/status`.
- After connecting, the dashboard polls the ESP32 every 2 seconds.
- If the ESP32 disappears from Wi-Fi, the app automatically changes to disconnected/red state.
- Both ESP32 and browser device must be on the same Wi-Fi network.

## ESP32 API expected
GET `/api/status`

Example JSON:
```json
{
  "battery_soc": 78,
  "battery_health": 92,
  "battery_temperature": 29,
  "battery_voltage": 12.6,
  "charge_cycles": 143,
  "distance_km": 12.4,
  "speed_kmh": 18.5,
  "calories": 280,
  "energy_wh": 46.2,
  "power_w": 142,
  "cadence_rpm": 76
}
```

## Important browser/Wi-Fi note
A web page cannot reliably scan the local network to discover an ESP32 automatically. Enter the ESP32's local IP address (for example `192.168.1.50`) or `ecocharge.local` in the Connect dialog. The ESP32 should run an HTTP API and allow requests from the browser (CORS).

## Run
Open `index.html`. Click Connect, enter the ESP32 IP/hostname, and test the connection.
