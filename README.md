# SafeNest

### Intelligent Carbon Monoxide Monitoring and Early-Warning System

SafeNest is a personal engineering project designed to detect potentially
dangerous carbon monoxide concentrations and environmental changes, provide
local warnings, and remotely transmit an alert with a photograph.

The system combines two ESP32-based controllers, environmental sensors,
a camera module, an LCD interface, an audible alarm, UART communication,
Wi-Fi connectivity, and Telegram-based remote notification.

---

## Overview

SafeNest continuously monitors its environment using:

- MQ-9 carbon monoxide sensor
- DHT22 temperature and humidity sensor
- ESP32 DevKit V1
- AI-Thinker ESP32-CAM
- 20×4 I2C LCD
- Passive buzzer
- Wi-Fi
- Telegram notifications

When a potentially dangerous condition is detected, the system can:

1. Detect the abnormal sensor reading
2. Display the condition locally
3. Activate an audible warning
4. Communicate the alert to the camera controller
5. Capture a photograph
6. Send the photograph and alert information remotely

---

## System Architecture
             ┌─────────────────────┐
             │     MQ-9 Sensor     │
             └──────────┬──────────┘
                        │
             ┌──────────▼──────────┐
             │                     │
             │    ESP32 DevKit     │
             │    Main Controller  │
             │                     │
             └──────┬─────┬───────┘
                    │     │
             ┌──────▼─┐ ┌─▼────────┐
             │ DHT22  │ │ LCD 20×4 │
             └────────┘ └──────────┘
                    │
                ┌───▼───┐
                │ Buzzer│
                └───────┘
                    │
                 UART
                    │
             ┌──────▼──────────────┐
             │    ESP32-CAM        │
             │ Camera Controller   │
             └──────────┬──────────┘
                        │
                      Wi-Fi
                        │
                ┌───────▼────────┐
                │    Telegram    │
                └────────────────┘
                ┌───────▼────────┐
                │    Telegram    │
                └────────────────┘
