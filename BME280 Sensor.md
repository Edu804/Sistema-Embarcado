# Introdução

O BME280 é um sensor versátil que realiza leituras de: 

- Temperatura
- Pressão Barométrica
- Umidade

Ele se comunica com o Raspberry Pi via I²C, utilizando o endereço 0x76. Este sensor opera com uma tensão de alimentação VCC de 3V. 

**Imagem ilustrativa do sensor BME280:** 

<img src="https://github.com/user-attachments/assets/8659d61b-ad94-4567-bb5c-6dbccf01b21f" width="300" height="200" />


Para mais informações técnicas, consulte o [datasheet do BME280](https://www.mouser.com/datasheet/2/783/BST-BME280-DS002-1509607.pdf?srsltid=AfmBOop-gdYKkXnbAD9bpCml_pHpVhmNiTOP9BESw5skehoDlsiTTI81).

## Configuração no Raspberry Pi

Para utilizar o BME280, siga as etapas abaixo para ativar a interface I²C e instalar as bibliotecas necessárias: 

1. Clique no ícone do Raspberry Pi (imagem de uma framboesa).
2. Navegue até **Preferências** → **Configuração do Raspberry Pi**.
3. Na aba **Interface**, ative a opção **I²C**.
4. Reinicie o Raspberry Pi para aplicar as configurações.

### Instalação das Bibliotecas

Atualize o sistema e instale as bibliotecas necessárias para o sensor:

```bash
sudo apt update
sudo apt install python3-pip
pip3 install adafruit-circuitpython-bme280
```
## Leitura dos Dados

Utilize o seguinte código em Python para obter leituras de temperatura, pressão e umidade:

```python
import time
import board
import busio
from adafruit_bme280 import basic as adafruit_bme280

# Inicializa o barramento I²C
i2c = busio.I2C(board.SCL, board.SDA)

# Inicializa o sensor BME280 com o endereço padrão 0x76
bme280 = adafruit_bme280.Adafruit_BME280_I2C(i2c, address=0x76)

def sensor_bme280():
    # Lê os dados do sensor
    temperature_celsius = bme280.temperature
    pressure = bme280.pressure
    humidity = bme280.humidity

    return humidity, pressure, temperature_celsius
```
### Interpretação dos Dados

Ao chamar a função `sensor_bme280()`, os valores retornados representam, respectivamente:

- Umidade (% relativa)
- Pressão (hPa)
- Temperatura (°C)

Este sensor é amplamente utilizado em projetos que exigem monitoramento ambiental, como estações meteorológicas, controle de ventilação, entre outros.
