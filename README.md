## Procedimientos para instalar y ejecutar Servidor Web IoT Wokwi (VSCode)

1. PlatformIO IDE (platformio.org). Crear proyecto, compilar el binario
2. Wokwi (Simulador Web ejecutándose local). Solicitará una licencia que podrá activar utilizando su cuenta de GMAIL 

*<<< Reiniciar VSCode >>>*
    
3. Crear proyecto en PlatformIO > ESP32
```
Name: ESP32-IOT (libre según usuario)
Board: Espressif ESP32 Dev module
Framework: Arduino
```
  _<<< Tiempo 5 - 10 minutos >>>_

4. Configurando el proyecto - platformio.ini
```
monitor_speed = 115200
```

5. Código (ino > main.cpp)
  Nota: No elimines **#include <Arduino.h>**
  Reemplazar todo el código desde la línea 2 en adelante

6. Compilar el código. PlatformIO Build > Successfully created esp32 image.

7. Crear en la raíz del proyecto **"diagram.json"**, clic derecho abrir con editor. Pegar el contenido del archivo **diagram.json** de wokwi (Web)

8. Víncular el binario generado con la interfaz. Crear el archivo **wokwi.toml** -> https://docs.wokwi.com/vscode/project-config

```
[wokwi]
version = 1
firmware = '.pio\build\esp32dev\firmware.bin'
elf = '.pio\build\esp32dev\firmware.elf'

# Forward http://localhost:8180 to port 80 on the simulated ESP32:
[[net.forward]]
from = "localhost:8180"
to = "10.13.37.2:80"
```
9. Ejecutar el archivo diagram.json en un navegador escribir: **localhost:8180**
