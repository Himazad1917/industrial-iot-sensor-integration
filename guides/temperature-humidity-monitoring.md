# Temperature & Relative-Humidity Monitoring — Integration Guide

This guide outlines a vendor-neutral approach to integrating temperature and relative-humidity (RH) sensors into an industrial monitoring system. It is not a wiring guide for a particular model.

## Typical architecture

~~~mermaid
flowchart LR
  A[T/RH sensor] --> B[Local interface: analogue / RS485 / wireless]
  B --> C[Controller or gateway]
  C --> D[Data validation and timestamps]
  D --> E[Dashboard / historian / alerting]
~~~

## Before installation

- Identify the exact sensor model and approved supply voltage.
- Confirm the output: 4–20 mA, voltage, RS485/Modbus RTU, or a wireless protocol.
- Record range, accuracy, response time, ingress protection, operating environment, and calibration status from the datasheet.
- Select a representative location; avoid unintended heat sources, direct solar heating, stagnant pockets, and locations outside the sensor's rating.
- For duct sensors, follow the manufacturer's insertion-depth, orientation, and sealing guidance.

## Data model

Use explicit units and metadata rather than ambiguous names.

~~~json
{
  "timestamp": "2026-01-01T12:00:00Z",
  "temperature_c": 24.6,
  "relative_humidity_pct": 48.2,
  "sensor_id": "example-sensor-01",
  "quality": "illustrative"
}
~~~

All values above are illustrative sample data, not real measurements.

## Validation checklist

1. Compare the installed location and orientation with the datasheet.
2. Confirm units, scaling, and sensor range at the controller.
3. Check for missing, stale, out-of-range, or implausibly fast-changing values.
4. Use a suitable reference instrument and an agreed acceptance tolerance when verifying readings.
5. Record the comparison conditions and calibration status.
6. Configure communication-loss and sensor-fault alerts where supported.

## Troubleshooting

| Symptom | Possible checks |
|---|---|
| RH fixed at one value | Sensor configuration, communication quality, update interval, environmental conditions |
| Temperature offset | Sensor placement, self-heating, reference method, wiring/scaling, calibration status |
| Intermittent readings | Supply stability, cable routing, connector condition, bus termination/topology where applicable |
| Condensation or contamination | Check model rating and installation guidance; follow approved cleaning/service instructions |

## Safety and limits

Follow the instrument manual, site electrical rules, and applicable environmental requirements. Do not assume all T/RH sensors share the same wiring, Modbus registers, or calibration procedure.

## Further reading

- [KLED Measurement official website](https://www.kledmeasurement.in/)
- [Modbus specifications](https://www.modbus.org/specs.php) (for models that explicitly support Modbus)

This is a general educational guide; no field installation or device test is claimed.