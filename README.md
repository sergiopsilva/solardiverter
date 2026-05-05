# ☀️ SolarDiverter

**Intelligent surplus solar energy diverter for ESP32**

**Controlador inteligente de desvio de excedente solar para ESP32**

> 🔓 **Firmware livre para uso pessoal. A ativação é obrigatória.**  
> A versão **LITE é gratuita**, mas só é ativada após contacto através do site oficial.
>
> 🔓 **Free firmware for personal use. Activation is required.**  
> The **LITE version is free**, but only activated after contacting through the official website.

---

## O que é?

O **SolarDiverter** não é apenas mais um gestor de excedentes. É um **controlador inteligente** que transforma o excedente solar em energia útil, ajustando a potência de forma **dinâmica, segura e eficiente** — muito além do simples "liga/desliga".

**Torna o seu termoacumulador inteligente**: em vez de apenas ligar/desligar, ajusta a potência de forma proporcional ao excedente disponível, maximizando a utilização da energia solar.

Desvia automaticamente cada watt que seria exportado para a rede para cargas resistivas como termoacumuladores, resistências de aquecimento e toalheiros elétricos.

Baseado num **ESP32-WROOM-32U**, é configurado inteiramente via **Web UI**, sem necessidade de programação. Monitoriza medidores Shelly EM / 3EM ou inversores Modbus RTU, ajusta o PWM proporcional ao excedente e integra-se com domótica via MQTT.

**Funcionalidades avançadas incluídas:**
- Controlo inteligente por temperatura (DS18B20)
- Boost temporizado
- Agendamentos otimizados para tarifas Bi/Tri-horárias
- Modulação PWM proporcional ao excedente

### Mesmo sem painéis solares?

**Sim!** O SolarDiverter pode ser usado como **alternativa económica a termoacumuladores inteligentes** caros. Mesmo sem fotovoltaico, permite:

- **Agendamentos por horários** — aquece apenas quando necessário
- **Tarifas Bi/Tri-horárias** — aproveita períodos de energia mais barata
- **Temperaturas personalizáveis** — controlo preciso por sensor DS18B20
- **Controlo remoto via MQTT** — integração com domótica

Transforma qualquer termoacumulador tradicional num dispositivo inteligente, a uma fração do custo.

## What is it?

**SolarDiverter** is not just another surplus diverter. It is an **intelligent controller** that converts surplus solar energy into useful heat with **dynamic, safe and temperature-aware modulation** — far beyond simple on/off switching.

**Makes your water heater smart**: instead of just switching on/off, it adjusts power proportionally to available surplus, maximizing solar energy usage.

It automatically diverts every excess watt to resistive loads such as water heaters, heating elements and towel rails.

Built on an **ESP32-WROOM-32U**, it is fully configured through a **Web UI**, with no coding required. It monitors Shelly EM / 3EM meters or Modbus RTU inverters, adjusts PWM proportionally to surplus, and integrates with home automation via MQTT.

**Advanced features include:**
- Temperature-aware smart control (DS18B20)
- Timed Boost mode
- Optimised scheduling for Bi/Tri-hourly tariffs
- Proportional PWM modulation

### Even without solar panels?

**Yes!** SolarDiverter can be used as a **cost-effective alternative to expensive smart water heaters**. Even without photovoltaic panels, it enables:

- **Time-based scheduling** — heat only when needed
- **Bi/Tri-hourly tariffs** — take advantage of cheaper energy periods
- **Customizable temperatures** — precise control via DS18B20 sensor
- **Remote control via MQTT** — home automation integration

Transforms any traditional water heater into a smart device, at a fraction of the cost.

---

## Ativação e Versões / Activation and Versions

### Estados de Funcionamento

O SolarDiverter funciona em **três estados**:

1. **Antes da ativação** — modo limitado (teste inicial)
2. **LITE ativada** — gratuita, funcional para uso doméstico
3. **PRO ativada** — paga, com funcionalidades avançadas

**Todas as ativações** (Lite e Pro) são feitas por **chave digital** e requerem pedido via email.

**Versão LITE gratuita**: Pedido através do site oficial → https://sergiopsilva.github.io/solardiverter-site/

**Versão PRO paga**: A chave é gerada com base no **Chip ID** do dispositivo.

### Operating States

The SolarDiverter operates in **three states**:

1. **Before activation** — restricted mode (initial testing)
2. **LITE activated** — free, functional for home use
3. **PRO activated** — paid, with advanced features

**All activations** (Lite and Pro) use a **digital key** and require a request via email.

**Free LITE version**: Request through official website → https://sergiopsilva.github.io/solardiverter-site/

**Paid PRO version**: Key is generated based on the device's **Chip ID**.

---

### Antes da ativação (modo limitado)

Quando o firmware é instalado pela primeira vez, funciona em **modo restrito**:

- PWM limitado a **40%**
- Apenas **1 canal** ativo
- Agendamentos desativados
- Modbus desativado
- MQTT parcial
- Apenas **1 sensor** DS18B20
- Algumas proteções e funções avançadas indisponíveis

Serve apenas para **teste inicial e validação do hardware**.

### Before activation (restricted mode)

When first installed, the firmware runs in **restricted mode**:

- PWM limited to **40%**
- Only **1 channel** active
- Scheduling disabled
- Modbus disabled
- Partial MQTT
- Only **1 DS18B20** sensor
- Some protections and advanced features unavailable

Intended only for **initial testing and hardware validation**.

---

## Versões / Versions — LITE vs PRO

### LITE — Restrições

| Estado | Não ativada | Ativada |
|--------|-------------|---------|
| **PWM canais físicos** | 1 (sempre) | 1 (sempre) |
| **PWM manual (slider)** | Máx 60% (153/255) | 100% (255/255) |
| **PWM auto (slider)** | Máx 60% (153/255) | 100% (255/255) |
| **Agendamento card 0** | Desabilitado | Habilitado |
| **Agendamento card 1** | Oculto | Visível |
| **Agendamento cards 2–3** | Sempre ocultos | Sempre ocultos |
| **Sensor ambiente (env)** | Oculto | Visível |
| **Sensor extra (nome + grupo)** | Oculto | Visível |
| **Sensor água + TRIAC** | Sempre visível | Sempre visível |
| **Modbus scanner** | Oculto (PRO-only) | Oculto (PRO-only) |
| **Banner "Ativar"** | Visível | Oculto |

### PRO — Restrições

| Estado | Não ativada | Ativada |
|--------|-------------|---------|
| **PWM canais físicos** | 4 (sempre) | 4 (sempre) |
| **PWM manual (slider)** | Máx 60% (153/255) | 100% (255/255) |
| **PWM auto (slider)** | Máx 60% (153/255) | 100% (255/255) |
| **Agendamento card 0** | Habilitado | Habilitado |
| **Agendamento cards 1–3** | Ocultos | Visíveis |
| **Tarifário Horário (Bi/Tri)** | Oculto | Visível |
| **Sensor ambiente (env)** | Oculto | Visível |
| **Sensor extra (nome + grupo)** | Oculto | Visível |
| **Sensor água + TRIAC** | Sempre visível | Sempre visível |
| **Modbus scanner** | Oculto | Visível |
| **Banner "Ativar"** | Visível | Oculto |

### Diferenças LITE vs PRO (ambas ativadas)

**LITE (ativada)**
- 1 canal PWM
- 2 agendamentos (card 0 + card 1)
- Sem tarifário horário
- Sem Modbus scanner
- Adequado para uso doméstico simples

**PRO (ativada)**
- 4 canais PWM independentes
- 4 agendamentos completos
- Tarifário Bi/Tri-horário
- Modbus scanner incluído
- Controlo mais eficiente e flexível para gestão de excedentes
- Ideal para instalações profissionais ou setups complexos

### Formas de obter a versão PRO

1. **Hardware pronto a ligar**
   - Enviado já ativado como PRO
   - Não é necessário inserir chave

2. **Kit DIY com ESP incluído**
   - ESP segue com Chip ID conhecido
   - Chave PRO gerada e ativada antes do envio
   - Firmware arranca já em modo PRO

3. **Ativação PRO em hardware próprio**
   - Utilizador fornece o Chip ID
   - Compra apenas a chave PRO
   - Recebe a chave digital por email

---

## Comparação Técnica / Technical Comparison

Disponível em duas versões com funcionalidades distintas:
Available in two versions with distinct feature sets:

| | LITE | PRO |
|---|---|---|
| **Canais PWM** | 1 | 4 (independentes) |
| **PWM máximo (ativado)** | 100% | 100% |
| **Agendamentos** | 2 (cards 0 e 1) | 4 (com janela de temperatura) |
| **Tarifário Bi/Tri-horário** | Não | Sim |
| **Sensores DS18B20** | Água, TRIAC, Ambiente, Extra | Água, TRIAC, Ambiente, Extra 1-5 |
| **Peak Shaving** | Sim | Sim |
| **Battery Priority** | Sim | Sim |
| **MQTT** | Sim | Sim |
| **OTA (Web UI)** | Sim | Sim |
| **Proteção de fase** | Não | Sim (Shelly 3EM) |
| **Modbus Scanner** | Não | Sim |
| **Modbus Universal JSON** | Não | Sim |
| **Partição** | OTA (2x 1.5MB + 896KB SPIFFS) | OTA (2x 1.5MB + 896KB SPIFFS) |
| **Ativação** | Gratuita (requer registo) | Paga (chave Chip ID) |

> **LITE (ativada)** — 1 carga, 2 agendamentos, sensores completos. Prática e funcional para uso doméstico simples.
>
> **PRO (ativada)** — 4 cargas independentes, 4 agendamentos com controlo de temperatura, Modbus avançado, proteção por fase. Para instalações profissionais.

---

## Quick Start

### Flash via USB (Windows)

**Versão LITE:**
```bash
cd releases\v1.0.3-lite-beta
flash.bat COM4
```

**Versão PRO:**
```bash
cd releases\v1.3.2-pro
flash.bat COM4
```

### Primeira configuração

1. **Após flash**, o dispositivo cria um WiFi AP: **`SolarDiverter-Setup`**
2. Conecte-se ao WiFi (password: `12345678` ou sem password)
3. Aceda a `http://192.168.4.1`
4. Configure:
   - WiFi da sua rede
   - Medidor de energia (Shelly / Modbus)
   - MQTT (opcional)
5. **Guarde e reinicie**
6. O dispositivo conecta à sua rede WiFi

### Ativação

#### LITE (Gratuita)
1. Aceda ao dispositivo após configuração WiFi
2. No banner de ativação, copie o **Chip ID**
3. Registe-se em: https://sergiopsilva.github.io/solardiverter-site/
4. Receberá a chave por email
5. Introduza a chave na interface Web
6. Reinicie o dispositivo

#### PRO (Paga)
1. Contacte para adquirir chave PRO
2. Forneça o **Chip ID** do seu ESP32
3. Receberá a chave digital por email
4. Introduza a chave na interface Web
5. Reinicie o dispositivo

### Compilar (PlatformIO)

```bash
pio run                           # LITE
cd pro && pio run                 # PRO
```

---

## Funcionalidades / Features

- Controlo PWM proporcional ao excedente solar (rampa suave)
- Interface Web completa — sem necessidade de programação
- Shelly EM, Shelly 3EM (3 fases) e inversores Modbus RTU
- Sensores DS18B20 — monitorização e proteção térmica
- Display OLED — estado em tempo real
- MQTT — Home Assistant, Node-RED, etc.
- Proteção térmica TRIAC — corte automático a 65°C (configurável)
- Modo AP para setup inicial sem rede WiFi
- Watchdog de hardware para segurança operacional

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

**Uso pessoal, não comercial. Ativação obrigatória.**

- **LITE**: Gratuita com registo (chave fornecida após pedido)
- **PRO**: Paga (chave baseada no Chip ID do dispositivo)

Qualquer forma de venda, distribuição comercial ou inclusão em produtos comerciais é expressamente proibida sem autorização prévia por escrito do autor.

**Personal, non-commercial use only. Activation required.**

- **LITE**: Free with registration (key provided upon request)
- **PRO**: Paid (key based on device Chip ID)

Any form of sale, commercial distribution, or inclusion in commercial products is expressly prohibited without prior written authorization from the author.

© 2026 **AlternativaIOT** — Sérgio da Silva

---

## Contacto / Contact

**Pedidos de ativação LITE / LITE activation requests:**  
👉 https://sergiopsilva.github.io/solardiverter-site/

**Pedidos de ativação PRO / PRO activation requests:**  
📧 Email através do site oficial / Email through official website

**Suporte técnico / Technical support:**  
Abra uma issue no repositório / Open an issue on the repository
