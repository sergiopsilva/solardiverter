# SolarDiverter PRO - Flash Distribution

## Conteúdo
- `flash.bat` — Flash completo (firmware + SPIFFS + partições)
- `erase.bat` — Apagar flash do ESP32
- `firmware_pro.bin` — Firmware PRO
- `spiffs.bin` — SPIFFS com ficheiros web PRO
- `bootloader.bin`, `partitions.bin`, `boot_app0.bin` — Componentes de sistema
- `esptool.exe` — Ferramenta de flash

## Utilização
1. Ligue o ESP32 via USB
2. Execute `flash.bat COM10` (substitua COM10 pela porta correcta)
3. Aceda a http://192.168.4.1 para configurar o WiFi

## Versão PRO — v1.0.3
- 4 canais PWM independentes (GPIO 25, 26, 33, 5)
- PWM Auto até 100%
- 4 sondas de temperatura (triac + termoacumulador + ambiente + extra)
- 4 agendamentos com janela de temperatura
- Proteção de fase (Shelly 3EM)
- Modbus Scanner com auto-discovery
- Modbus Universal JSON (perfis de inversores)
- Partição huge_app (3 MB) — sem OTA
- Requer ativação por chave (Chip ID)
- Todas as protecções de segurança activas

## Passo a Passo (Windows)

### 1. Preparar o ESP32
- Ligue o ESP32 ao computador via cabo USB

### 2. Identificar a Porta COM
- Abra o **Gestor de Dispositivos** (Win+X → Gestor de Dispositivos)
- Expanda a secção **Portas (COM e LPT)**
- Procure o ESP32 (geralmente "USB-SERIAL CH340" ou "Silicon Labs CP210x")
- Anote o número da porta (ex: **COM4**)

> **⚠️ Não encontra a porta?**
> Instale os drivers:
> - CH340: https://sparks.gogo.co.nz/ch340.html
> - CP2102: https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers

### 3. Executar o Flash
Na janela de comandos, escreva:
```
flash.bat COMX
```
Substitua **X** pelo número da porta (ex: `flash.bat COM4`)

### 4. Modo Flash (se necessário)
Se aparecer erro de ligação:
- Mantenha pressionado o botão **BOOT** no ESP32
- Enquanto segura o BOOT, prima e liberte o botão **EN/RST** (se existir)
- Liberte o botão BOOT quando o flash começar

### 5. Aguardar
- O processo demora cerca de 1-2 minutos
- Quando terminar, aparece a mensagem "Hard resetting"
- O ESP32 reinicia automaticamente

## Após o Flash

1. Procure nas redes WiFi: **SolarDiverter-Setup**
2. Ligue-se à rede (não tem password)
3. Abre automaticamente a página de configuração (ou aceda a http://192.168.4.1)
4. Configure a sua rede WiFi e clique em **Guardar**

---

© 2026 AlternativaIOT - Sérgio da Silva | Uso pessoal, não comercial.
5. O dispositivo mostra o IP atribuído e redireciona automaticamente
6. Ligue-se à sua rede WiFi normal e aceda ao IP indicado

---

## Comandos Disponíveis

| Comando | Descrição |
|---------|-----------|
| `flash.bat COMX` | Flash completo (firmware + ficheiros web) |
| `erase.bat COMX` | Apagar toda a memória (reset de fábrica) |

---

## Ficheiros na Pasta

| Ficheiro | Descrição |
|----------|-----------|
| `firmware.bin` | Firmware principal |
| `spiffs.bin` | Páginas web e configurações |
| `bootloader.bin` | Bootloader do ESP32 |
| `partitions.bin` | Tabela de partições |
| `boot_app0.bin` | Selector de boot |

---

## Resolução de Problemas

### "Porta COM não encontrada"
- Verifique se o cabo USB transmite dados (não apenas carrega)
- Tente outra porta USB
- Instale os drivers acima indicados

### "Erro de permissão" ou falha de ligação
- Feche programas que usem a porta (TeraTerm, PuTTY, Arduino IDE, etc.)
- Use o botão BOOT conforme descrito no passo 5

### Flash falha repetidamente
1. Execute primeiro: `erase.bat COMX` 
2. Depois execute: `flash.bat COMX`

### Flash lento ou corrupto
- Abra `flash.bat` num editor de texto
- Altere `921600` para `115200` (velocidade mais lenta mas mais estável)

---

## Linux / Mac

```bash
chmod +x flash.sh erase.sh
./flash.sh /dev/ttyUSB0      # Flash completo
./erase.sh /dev/ttyUSB0      # Apagar flash
```

Se houver erro de permissão:
```bash
sudo usermod -a -G dialout $USER
# Fazer logout e login novamente
```

---

## Suporte

Em caso de dúvidas, consulte a documentação do projeto ou abra uma issue no repositório.

