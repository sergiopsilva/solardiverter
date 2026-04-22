☀️ SolarDiverter
Intelligent surplus solar energy diverter for ESP32  
Controlador inteligente de desvio de excedente solar para ESP32

🔓 Firmware livre para uso pessoal. A ativação é obrigatória.  
A versão LITE é gratuita, mas só é ativada após contacto através do site oficial.

🔓 Free firmware for personal use. Activation is required.  
The LITE version is free, but only activated after contacting through the official website.

🇵🇹 O que é?
O SolarDiverter não é apenas mais um gestor de excedentes.
É um controlador inteligente que transforma o excedente solar em energia útil, ajustando a potência de forma dinâmica, segura e eficiente — muito além do simples “liga/desliga”.

Desvia automaticamente cada watt que seria exportado para a rede para cargas resistivas como termoacumuladores, resistências de aquecimento e toalheiros elétricos.

Baseado num ESP32‑WROOM‑32U, é configurado inteiramente via Web UI, sem necessidade de programação. Monitoriza medidores Shelly EM / 3EM ou inversores Modbus RTU, ajusta o PWM proporcional ao excedente e integra‑se com domótica via MQTT.

Funcionalidades avançadas incluídas:

Controlo inteligente por temperatura (DS18B20)

Boost temporizado

Agendamentos otimizados para tarifas Bi/Tri-horárias

Modulação PWM proporcional ao excedente

🇬🇧 What is it?
SolarDiverter is not just another surplus diverter.
It is an intelligent controller that converts surplus solar energy into useful heat with dynamic, safe and temperature‑aware modulation — far beyond simple on/off switching.

It automatically diverts every excess watt to resistive loads such as water heaters, heating elements and towel rails.

Built on an ESP32‑WROOM‑32U, it is fully configured through a Web UI, with no coding required. It monitors Shelly EM / 3EM meters or Modbus RTU inverters, adjusts PWM proportionally to surplus, and integrates with home automation via MQTT.

Advanced features include:

Temperature‑aware smart control

Timed Boost mode

Optimised scheduling for Bi/Tri‑hourly tariffs

Proportional PWM modulation

🔐 Ativação e Versões / Activation and Versions
O SolarDiverter funciona em três estados:
The SolarDiverter operates in three states:

Antes da ativação — modo limitado

LITE ativada — gratuita

PRO ativada — paga, com funcionalidades avançadas

Todas as ativações (Lite e Pro) são feitas por chave digital e requerem pedido via email.
All activations (Lite and Pro) use a digital key and require a request via email.

A versão LITE é gratuita, mas só é ativada após contacto através do site oficial:
👉 https://sergiopsilva.github.io/solardiverter-site/

A versão PRO é paga, e a chave é gerada com base no Chip ID do dispositivo.
The PRO version is paid, and the key is generated based on the device’s Chip ID.

🇵🇹 Antes da ativação (modo limitado)
🇬🇧 Before activation (restricted mode)
Quando o firmware é instalado pela primeira vez, funciona em modo restrito:
When first installed, the firmware runs in a restricted mode:

PWM limitado (40%)

Apenas 1 canal ativo

Agendamentos desativados

Modbus desativado

MQTT parcial

Apenas 1 sensor DS18B20

Algumas proteções e funções avançadas indisponíveis

Serve apenas para teste inicial e validação do hardware.

🌟 LITE — Restrições
markdown
## LITE — Restrições

### Estado: Não ativada vs Ativada

| Item                           | Não ativada              | Ativada               |
|--------------------------------|---------------------------|------------------------|
| PWM canais físicos             | 1 (sempre)                | 1 (sempre)             |
| PWM manual (slider)            | Máx 60% (153/255)         | 100% (255/255)         |
| PWM auto (slider)              | Máx 60% (153/255)         | 100% (255/255)         |
| Agendamento card 0             | Desabilitado              | Habilitado             |
| Agendamento card 1             | Oculto                    | Visível                |
| Agendamento cards 2–3          | Sempre ocultos            | Sempre ocultos         |
| Sensor ambiente (env)          | Oculto                    | Visível                |
| Sensor extra (nome + grupo)    | Oculto                    | Visível                |
| Sensor água + TRIAC            | Sempre visível            | Sempre visível         |
| Modbus scanner                 | Oculto (PRO-only)         | Oculto (PRO-only)      |
| Banner "Ativar"                | Visível                   | Oculto                 |
🚀 PRO — Restrições
markdown
## PRO — Restrições

### Estado: Não ativada vs Ativada

| Item                           | Não ativada              | Ativada               |
|--------------------------------|---------------------------|------------------------|
| PWM canais físicos             | 4 (sempre)                | 4 (sempre)             |
| PWM manual (slider)            | Máx 60% (153/255)         | 100% (255/255)         |
| PWM auto (slider)              | Máx 60% (153/255)         | 100% (255/255)         |
| Agendamento card 0             | Habilitado                | Habilitado             |
| Agendamento cards 1–3          | Ocultos                   | Visíveis               |
| Tarifário Horário (Bi/Tri)     | Oculto                    | Visível                |
| Sensor ambiente (env)          | Oculto                    | Visível                |
| Sensor extra (nome + grupo)    | Oculto                    | Visível                |
| Sensor água + TRIAC            | Sempre visível            | Sempre visível         |
| Modbus scanner                 | Oculto                    | Visível                |
| Banner "Ativar"                | Visível                   | Oculto                 |
🔎 Diferenças LITE vs PRO (ambas ativadas)
markdown
## Diferenças LITE vs PRO (ambas ativadas)

### LITE (ativada)
- 1 canal PWM
- 2 agendamentos (card 0 + card 1)
- Sem tarifário horário
- Sem Modbus scanner
- Adequado para uso doméstico simples

### PRO (ativada)
- 4 canais PWM independentes
- 4 agendamentos completos
- Tarifário Bi/Tri-horário
- Modbus scanner incluído
- Controlo mais eficiente e flexível para gestão de excedentes
- Ideal para instalações profissionais ou setups complexos
🧩 Formas de obter a versão PRO
1. Hardware pronto a ligar
Enviado já ativado como PRO

Não é necessário inserir chave

2. Kit DIY com ESP incluído

ESP segue com Chip ID conhecido

Chave PRO gerada e ativada antes do envio

Firmware arranca já em modo PRO

3. Ativação PRO em hardware próprio
Utilizador fornece o Chip ID

Compra apenas a chave PRO

Recebe a chave digital por email

<img width="1169" height="826" alt="Schematic_dimmerSOLARDIV_2026-04-21" src="https://github.com/user-attachments/assets/ebd2afeb-a4bb-41d2-b849-e419f1487d43" />

<img width="847" height="552" alt="diagram" src="https://github.com/user-attachments/assets/7b97dc8e-ab0e-4539-acb4-a07a366bf06e" />

<img width="567" height="364" alt="SolarDiv esquema de ligação e wifi" src="https://github.com/user-attachments/assets/1b422b7c-2d59-4773-95f3-c2ce3939977c" />

<img width="530" height="699" alt="image1" src="https://github.com/user-attachments/assets/a6e8f910-ab7c-4ef7-a0e8-10dd57d33d1b" />
<img width="733" height="805" alt="PCB" src="https://github.com/user-attachments/assets/5e8c0a47-f807-46ee-b246-8a1608dfcd07" />
<img width="525" height="574" alt="image2" src="https://github.com/user-attachments/assets/4f840754-f6b1-4726-8347-01ef16610e3f" />


