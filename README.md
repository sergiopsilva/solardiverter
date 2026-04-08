# ☀️ SolarDiverter

**Intelligent surplus solar energy diverter for ESP32**

**Controlador inteligente de desvio de excedente solar para ESP32**

> 🔓 **Firmware livre para uso pessoal.** Não pode ser vendido, redistribuído comercialmente ou incluído em produtos comerciais sem autorização escrita do autor.
>
> 🔓 **Free firmware for personal use.** It may not be sold, commercially redistributed or bundled into commercial products without the author's written permission.

---

## 🇵🇹 O que é?

O **SolarDiverter** transforma o excedente da sua instalação solar em energia útil. Em vez de injetar na rede a preço reduzido (ou zero), o controlador desvia automaticamente cada watt em excesso para cargas resistivas — termoacumuladores, resistências de aquecimento, toalheiros elétricos.

Baseado num **ESP32-WROOM-32U**, configura-se inteiramente por interface Web, sem programação. Monitoriza medidores Shelly EM / 3EM ou inversores Modbus RTU, ajusta o PWM de forma proporcional ao excedente e integra-se com domótica via MQTT.

## 🇬🇧 What is it?

**SolarDiverter** turns your surplus solar production into useful energy. Instead of exporting to the grid at low (or zero) rates, it automatically diverts every excess watt to resistive loads — water heaters, heating elements, towel rails.

Built on an **ESP32-WROOM-32U**, it's fully configured via a Web interface — no coding required. It monitors Shelly EM / 3EM meters or Modbus RTU inverters, adjusts PWM proportionally to surplus, and integrates with home automation via MQTT.

---

## Versões / Versions — LITE vs PRO

Disponível em duas versões com funcionalidades distintas:
Available in two versions with distinct feature sets:

| | LITE | PRO |
|---|---|---|
| **Canais PWM** | 1 | 4 (independentes) |
| **PWM Auto máx.** | 80% | 100% |
| **Agendamentos** | 1 (simples) | 4 (com janela de temperatura) |
| **Sensores DS18B20** | 2 | 4 |
| **Peak Shaving** | ✅ | ✅ |
| **Battery Priority** | ✅ | ✅ |
| **MQTT** | ✅ | ✅ |
| **OTA (Web UI)** | ✅ | ❌ |
| **Proteção de fase** | ❌ | ✅ (Shelly 3EM) |
| **Modbus Scanner** | ❌ | ✅ |
| **Modbus Universal JSON** | ❌ | ✅ |
| **Partição** | 1.5 MB (com OTA) | 3 MB (huge_app) |
| **Ativação** | Livre | Chave (Chip ID) |

> **LITE** — 1 carga, 1 agendamento, OTA disponível. Prática e funcional para uso doméstico simples.
>
> **PRO** — 4 cargas independentes, agendamentos com controlo de temperatura, Modbus avançado, proteção por fase. Para instalações profissionais.

---

## Quick Start

### Flash via USB (Windows)

```
espflash_lite\flash.bat COM4      ← versão LITE
espflash_pro\flash.bat COM4       ← versão PRO
```

### Primeira configuração

1. Ligue-se ao WiFi **SolarDiverter-Setup**
2. Aceda a `http://192.168.4.1`
3. Configure WiFi, medidor de energia e MQTT
4. Guarde e reinicie

### Compilar (PlatformIO)

```bash
pio run                           # LITE
cd pro && pio run                 # PRO
```

---

## Funcionalidades / Features

- ⚡ Controlo PWM proporcional ao excedente solar (rampa suave)
- 🌐 Interface Web completa — sem necessidade de programação
- 📡 Shelly EM, Shelly 3EM (3 fases) e inversores Modbus RTU
- 🌡️ Sensores DS18B20 — monitorização e proteção térmica
- 📟 Display OLED — estado em tempo real
- 🔌 MQTT — Home Assistant, Node-RED, etc.
- 🛡️ Proteção térmica TRIAC — corte automático a 65°C (configurável)
- 📶 Modo AP para setup inicial sem rede WiFi
- 🔄 Watchdog de hardware para segurança operacional

---

## Hardware

**ESP32-WROOM-32U** — pinout fixo:

| Função | GPIO |
|---|---|
| PWM (carga) | 25 |
| DS18B20 (OneWire) | 2 |
| OLED SDA / SCL / RST | 4 / 15 / 16 |
| Botão | 0 |
| LED Status | 32 |
| Modbus TX / RX | 17 / 16 |

---

## Estrutura / Structure

```
SolarDiverter/
├── src/                    # Código-fonte LITE
├── include/                # Headers LITE
├── data/                   # Web UI (HTML/CSS/JS)
├── pro/                    # Código-fonte + headers PRO
├── espflash_lite/          # Binários + flash script LITE
├── espflash_pro/           # Binários + flash script PRO
└── platformio.ini          # Configuração PlatformIO
```

---

## Licença / License

**Uso pessoal, não comercial.**
Qualquer forma de venda, distribuição comercial ou inclusão em produtos comerciais é expressamente proibida sem autorização prévia por escrito do autor.

**Personal, non-commercial use only.**
Any form of sale, commercial distribution, or inclusion in commercial products is expressly prohibited without prior written authorization from the author.

© 2026 **AlternativaIOT** — Sérgio da Silva

---

## Contacto / Contact

Para dúvidas, sugestões ou pedidos de licenciamento, abra uma issue no repositório.
For questions, suggestions, or licensing inquiries, open an issue on the repository.
