
☀️ SolarDiverter
Intelligent surplus solar energy diverter for ESP32  
Controlador inteligente de desvio de excedente solar para ESP32

> 🔓 Firmware livre para uso pessoal. A ativação é obrigatória. A versão LITE é gratuita, mas só é ativada após contacto através do site oficial.  
> 🔓 Free firmware for personal use. Activation is required. The LITE version is free, but only activated after contacting through the official website.

---

🇵🇹 O que é?

O SolarDiverter transforma o excedente da sua instalação solar em energia útil, desviando automaticamente cada watt que seria exportado para a rede para cargas resistivas — termoacumuladores, resistências de aquecimento, toalheiros elétricos.

Baseado num ESP32-WROOM-32U, é configurado inteiramente via Web UI, sem necessidade de programação. Monitoriza medidores Shelly EM / 3EM ou inversores Modbus RTU, ajusta o PWM proporcionalmente ao excedente e integra-se com domótica via MQTT.

🇬🇧 What is it?

SolarDiverter turns your surplus solar production into useful energy by automatically diverting every excess watt to resistive loads — water heaters, heating elements, towel rails.

Built on an ESP32-WROOM-32U, it is fully configured through a Web UI with no coding required. It monitors Shelly EM / 3EM meters or Modbus RTU inverters, adjusts PWM proportionally to surplus, and integrates with home automation via MQTT.

---

🔐 Ativação e Versões / Activation and Versions

O SolarDiverter funciona em três estados:

1) Antes da ativação — modo limitado
    
3) LITE ativada — gratuita  
4) PRO ativada — paga, com funcionalidades avançadas

Todas as ativações (Lite e Pro) são feitas por chave digital e requerem pedido via email.

A versão LITE é gratuita, mas só é ativada após contacto através do site oficial:  
👉 https://sergiopsilva.github.io/solardiverter-site/

A versão PRO é paga, e a chave é gerada com base no Chip ID do dispositivo.

---

🇵🇹 Antes da ativação (modo limitado)

Quando o firmware é instalado pela primeira vez, funciona em modo restrito:

- PWM limitado (40%)  
- Apenas 1 canal ativo  
- Agendamentos desativados  
- Modbus desativado  
- MQTT parcial  
- Apenas 1 sensor DS18B20  
- Algumas proteções e funções avançadas indisponíveis  

Este modo serve apenas para teste inicial e validação do hardware.

🇬🇧 Before activation (restricted mode)

When first installed, the firmware runs in a restricted mode:

- PWM limited (40%)  
- Only 1 active channel  
- Scheduling disabled  
- Modbus disabled  
- Partial MQTT  
- Only 1 DS18B20 sensor  
- Some protections and advanced features unavailable  

This mode is intended for initial testing and hardware validation.

---

🌟 LITE (ativada) — gratuita

🌟 LITE (activated) — free

A versão LITE é totalmente gratuita, mas requer pedido de ativação via site.  
Após ativação:

- PWM aumenta para 80%  
- 1 canal funcional  
- 1 agendamento simples disponível  
- 2 sensores DS18B20  
- MQTT completo  
- Modbus básico  
- OTA disponível (Web UI)  
- Adequado para uso doméstico simples  

A LITE remove as limitações essenciais, mantendo o projeto acessível a todos.

---

🚀 PRO (ativada) — paga

🚀 PRO (activated) — paid

A versão PRO desbloqueia todas as funcionalidades avançadas:

- 4 canais PWM independentes  
- PWM até 100%  
- 4 agendamentos avançados com janelas de temperatura  
- 4 sensores DS18B20  
- Modbus completo (Scanner + Universal JSON)  
- Proteção por fase (Shelly 3EM)  
- Partição huge_app (3 MB)  
- Ideal para instalações profissionais ou setups complexos  

A chave PRO é digital, não transferível e associada ao Chip ID.

---

🧩 Formas de obter a versão PRO

A versão PRO pode ser adquirida de três formas:

1) Hardware pronto a ligar
- O dispositivo é enviado já ativado como PRO  
- Não é necessário inserir chave  

2) Kit DIY com ESP incluído
- O ESP segue com Chip ID conhecido  
- A chave PRO é gerada e ativada antes do envio  
- O firmware arranca já em modo PRO  

3) Ativação PRO em hardware próprio
- O utilizador fornece o Chip ID  
- Compra apenas a chave PRO  
- Recebe a chave digital por email
-  
<img width="1169" height="826" alt="Schematic_dimmerSOLARDIV_2026-04-21" src="https://github.com/user-attachments/assets/ebd2afeb-a4bb-41d2-b849-e419f1487d43" />

<img width="847" height="552" alt="diagram" src="https://github.com/user-attachments/assets/7b97dc8e-ab0e-4539-acb4-a07a366bf06e" />
