# Industrial IoT Sensor Integration

A learning repository describing how industrial sensor data can travel from a sensor through an interface or controller to a gateway and application. This is a **conceptual reference**, not a claim of a completed field deployment.

## Purpose
Understand the layers in a typical industrial IoT monitoring solution and the questions to resolve during integration.

## Reference architecture

~~~mermaid
flowchart LR
  A[Sensor / transmitter] --> B[Interface or controller]
  B --> C[Gateway]
  C --> D[Network / broker / API]
  D --> E[Dashboard / historian / alerts]
~~~

## Guides and projects

- [Temperature & RH Monitoring](guides/temperature-humidity-monitoring.md) — installation planning, data quality, validation and troubleshooting
- [Industrial Sensor Documentation Template](guides/industrial-sensor-documentation-template.md) — reusable model/specification and commissioning template
- [KLED-70 NIR Moisture Transmitter Study](projects/kled-70-nir-moisture-transmitter/README.md) — overview based on KLED's public product page, integration questions and validation checklist

## Integration checklist

1. Identify exact model, variant, datasheet, output type, power requirements, and environmental limits.
2. Confirm the interface and protocol separately. RS485 is an electrical interface; Modbus RTU is a protocol.
3. Verify wiring, grounding, shielding, termination, and supply using the exact device manual.
4. Validate units, scaling, timestamps, data quality, and expected update interval.
5. Test communication loss and recovery in a controlled environment.
6. Keep passwords, tokens, keys, customer details, and proprietary configuration out of public repositories.

## Illustrative sample data

~~~json
{
  "timestamp": "2026-01-01T12:00:00Z",
  "temperature_c": 24.6,
  "relative_humidity_pct": 48.2,
  "quality": "illustrative"
}
~~~

These values are examples only and are not readings from a deployed device.

## Troubleshooting prompts

| Symptom | First checks |
|---|---|
| No values | Power, interface type, wiring, device address, settings and gateway logs |
| Wrong scale | Units, engineering range, input mode and manufacturer scaling documentation |
| Intermittent data | Supply, cabling, interference, topology, timeouts and logs |
| Values look plausible but wrong | Sensor placement, calibration, reference method and process conditions |

## Scope and references

This repository is educational. It does not claim physical hardware testing, customer deployment, or manufacturer endorsement. Use the current product manual and site safety procedures for actual installation.

- [KLED Measurement](https://www.kledmeasurement.in/)
- [Modbus specifications](https://www.modbus.org/specs.php)