# ☀️ SolarDiverter

**Solar Diverter — the surplus‑photovoltaic intelligent diverter**

**Controlador inteligente de desvio de energia solar para cargas resistivas**

> ⚠️ **Firmware livre para uso pessoal.** A distribuição ou utilização comercial deste software é proibida sem autorização prévia por escrito do autor.
>
> ⚠️ **Free firmware for personal use.** Commercial distribution or use of this software is prohibited without prior written authorization from the author.

---

## 🇵🇹 Português

O **SolarDiverter** é um controlador open-hardware baseado em ESP32 que monitoriza a produção solar e o consumo da rede em tempo real, desviando automaticamente o excedente de energia para cargas resistivas — como termoacumuladores, resistências de aquecimento ou toalheiros elétricos.

Em vez de injetar na rede a preço reduzido (ou zero), o SolarDiverter garante que cada watt produzido em excesso é aproveitado localmente, reduzindo a fatura energética e maximizando o retorno do investimento solar.

**Principais vantagens:**
- Controlo PWM proporcional ao excedente — sem desperdício, sem cortes bruscos
- Configuração via interface Web — sem necessidade de programação
- Compatível com medidores Shelly EM / 3EM e inversores Modbus RTU
- Monitorização de temperatura com sensores DS18B20
- Integração domótica via MQTT (Home Assistant, Node-RED, etc.)
- Display OLED local para visualização rápida do estado

### Versão LITE

A versão **LITE** é pensada para instalações simples com uma única carga resistiva. Controla 1 canal PWM, suporta 1 agendamento, e inclui atualização OTA pela interface Web — ideal para quem quer uma solução prática e funcional sem complexidade extra.

### Versão PRO

A versão **PRO** destina-se a instalações avançadas com múltiplas cargas. Controla até 4 canais PWM independentes, com 4 agendamentos programáveis com janela de temperatura, proteção por fase (Shelly 3EM), scanner Modbus com auto-discovery e suporte a perfis de inversores via JSON universal. Requer ativação por chave (Chip ID).

---

## 🇬🇧 English

**SolarDiverter** is an open-hardware ESP32-based controller that monitors solar production and grid consumption in real time, automatically diverting surplus energy to resistive loads — such as water heaters, heating elements, or towel rails.

Instead of exporting to the grid at reduced (or zero) rates, SolarDiverter ensures every excess watt is consumed locally, lowering your energy bill and maximizing your solar investment return.

**Key advantages:**
- Proportional PWM control matched to surplus — no waste, no hard switching
- Web-based configuration — no programming required
- Compatible with Shelly EM / 3EM meters and Modbus RTU inverters
- Temperature monitoring with DS18B20 sensors
- Home automation integration via MQTT (Home Assistant, Node-RED, etc.)
- Local OLED display for quick status overview

### LITE Version

The **LITE** version is designed for simple single-load installations. It controls 1 PWM channel, supports 1 schedule, and includes OTA updates via the Web UI — ideal for a practical, no-fuss setup.

### PRO Version

The **PRO** version targets advanced multi-load installations. It controls up to 4 independent PWM channels, with 4 programmable schedules including temperature windows, per-phase protection (Shelly 3EM), Modbus scanner with auto-discovery, and universal JSON inverter profiles. Requires key-based activation (Chip ID).

---

## Comparação / Comparison — LITE vs PRO

| Funcionalidade / Feature | LITE v1.0.3 | PRO v1.0.3 |
|---|---|---|
| **Canais PWM / PWM Channels** | 1 (GPIO 25) | 4 (GPIO 25, 26, 33, 5) |
| **PWM Auto — limite máx. / max limit** | 80% | 100% |
| **PWM Manual — limite máx. / max limit** | 100% | 100% |
| **Agendamentos / Schedules** | 1 (sem temperatura / no temp window) | 4 (com temperatura / with temp control) |
| **Sensores DS18B20** | até / up to 4 | até / up to 4 |
| **Peak Shaving** | ✅ | ✅ |
| **Battery Priority Mode** | ✅ | ✅ |
| **MQTT** | ✅ | ✅ |
| **OTA Update (Web UI)** | ✅ | ❌ (huge_app partition) |
| **Flash USB** | ✅ | ✅ |
| **Proteção de fase / Phase protection** | ❌ | ✅ (Shelly 3EM) |
| **Modbus Scanner (auto-discovery)** | ❌ | ✅ |
| **Modbus Universal JSON** | ❌ | ✅ |
| **Partição / Partition** | default (1.5 MB) | huge_app (3 MB) |
| **Ativação / Activation** | Livre / Free | Chave / Key (Chip ID) |

## Características

- **Suporte a múltiplos medidores de energia:**
  - Shelly EM (via HTTP)
  - Shelly 3EM (3 fases)
  - Inversores solares (Modbus RTU)

- **Interface Web** para configuração
- **Display OLED** para status local
- **Controlo PWM** de carga com rampa suave
- **3 sensores DS18B20** para monitorização térmica
- **4 saídas de relés** para controlo auxiliar
- **MQTT** para integração domótica
- **Watchdog** para segurança
- **Modo AP** para setup inicial sem WiFi

## Hardware

**ESP32-WROOM-32U** com pinout fixo:

| Função | GPIO |
|--------|------|
| PWM Output (carga) | 25 |
| OneWire (DS18B20) | 2 |
| OLED SDA | 4 |
| OLED SCL | 15 |
| OLED RST | 16 |
| Botão físico | 0 |
| LED Status | 32 |

| Modbus TX | 17 |
| Modbus RX | 16 |

## Estrutura do Projeto

```
SolarDiverter/
├── src/
│   ├── main.cpp                 # Entrada principal
│   ├── core/
│   │   ├── system_core.cpp      # Núcleo do sistema
│   │   └── watchdog.cpp         # Watchdog timer
│   ├── drivers/
│   │   ├── pwm_driver.cpp       # Controlo PWM
│   │   ├── temperature_sensor.cpp
│   │   ├── led_driver.cpp       # LED Status
│   │   ├── button_driver.cpp    # Botão com debounce
│   │   └── relay_driver.cpp     # Relés digitais
│   ├── comms/
│   │   ├── wifi_manager.cpp     # WiFi
│   │   ├── mqtt_manager.cpp     # MQTT
│   │   ├── http_server.cpp      # Web server
│   │   ├── shelly_em.cpp        # Shelly EM
│   │   ├── shelly_3em.cpp       # Shelly 3EM
│   │   └── inverter.cpp         # Modbus RTU
│   ├── ui/
│   │   └── oled_display.cpp     # Display OLED
│   └── tasks/
│       └── load_control.cpp     # Controlo de carga
├── include/
│   ├── pinout.h                 # Definições de pinos
│   ├── config.h                 # Estruturas de config
│   ├── system_state.h           # Estado global
│   ├── core/
│   ├── drivers/
│   ├── comms/
│   ├── ui/
│   └── tasks/
├── data/                        # Web UI (HTML, CSS, JS)
├── espflash_lite/               # Scripts e binários de flash LITE
├── platformio.ini               # Configuração PlatformIO
└── README.md                    # Este ficheiro
```

## Instalação e Compilação

### Pré-requisitos

- [PlatformIO](https://platformio.org/)
- Python 3.6+
- Visual Studio Code (opcional mas recomendado)

### Compilar

```bash
# Build completo
pio run

# Build para release
pio run -e esp32dev
```

### Flash

**Windows (LITE):**
```bash
espflash_lite\flash.bat COM3
```

Ou via PlatformIO:
```bash
pio run -t upload
```

## Configuração

### Primeira inicialização

1. **Sem WiFi configurado:** O ESP32 inicia em modo AP com SSID `SolarDiverter-Setup`
2. Conectar ao AP e aceder a `http://192.168.4.1`
3. Configurar WiFi, MQTT e medidores de energia
4. Reiniciar o dispositivo

### Parâmetros Principais

```cpp
// config.h
struct SystemConfig {
    WiFiConfig wifi;              // SSID/Password
    MQTTConfig mqtt;              // Broker MQTT
    ShellyEMConfig shelly_em;      // IP do Shelly EM
    Shelly3EMConfig shelly_3em;    // IP do Shelly 3EM
    InversorConfig inversor;       // Modbus (slave ID, baud)
    
    float excess_power_threshold_w = 100.0f;  // Min. para ativar
    float hysteresis_w = 50.0f;               // Histerese
};
```

## Operação

### Estados

- **SAFE_MODE**: LED a piscar (erro) - reconfiguração apenas
- **NORMAL**: Funcionamento normal - PWM controlado
- **SETUP**: Modo de configuração WiFi (botão pressionado)

### Botão de entrada

- **Curto**: Toggle entre NORMAL e SETUP
- **Longo (3s)**: Força reset

### Display OLED

Apresenta:
- Status WiFi
- Potência solar produzida
- Potência da rede (importação/exportação)
- PWM da carga

## Algoritmo de Controlo

```
Excedente = Produção Solar - Consumo da Rede

Se Excedente > (Threshold + Histerese):
    Aumentar PWM proporcionalmente
Se Excedente < (Threshold - Histerese):
    PWM = 0 (desligar)
Senão:
    Manter PWM anterior (histerese)
```

### Proteção Térmica

Se temperatura ambiente > 60°C:
- Reduzir PWM em 50%

## MQTT

Tópicos publicados:
- `SolarDiverter/status` - JSON com solar, grid, load
- `SolarDiverter/temp/1` - Temperatura sensor 1
- `SolarDiverter/temp/2` - Temperatura sensor 2
- `SolarDiverter/temp/3` - Temperatura sensor 3

## Expansões Futuras

- [ ] Histórico de produção/consumo
- [ ] Testes unitários
- [ ] Modo multi-zona (várias cargas) — disponivel na versão PRO

## Troubleshooting

### Display não aparece
- Verificar I2C (SDA=GPIO 4, SCL=GPIO 15)
- Verificar pull-ups nas linhas SDA/SCL

### WiFi não conecta
- Verificar SSID/Password
- Modo AP ativo? Desconectar e reiniciar

### Leitura de sensores falhando
- OneWire: verificar GPIO 2
- DS18B20: verificar pull-up (4.7k)

## Licença

Uso pessoal, não comercial. Qualquer forma de utilização comercial é expressamente proibida sem autorização prévia por escrito do autor.

© 2026 AlternativaIOT - Sérgio da Silva

## Contacto

Para dúvidas ou sugestões, abra uma issue no repositório.
