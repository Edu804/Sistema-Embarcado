# Introdução

O **K-33** da **SenseAir** é um sensor de dióxido de carbono (CO₂) que utiliza tecnologia **NDIR** (Infravermelho Não Dispersivo). Ele é projetado para medir concentrações de CO₂ em uma faixa de **0 - 5000 ppm** (podendo variar conforme o modelo). Suas principais características incluem: 

- **Precisão:** ±3% do valor medido.
- **Tempo de Resposta:** 20 segundos.

Este sensor opera com comunicação serial (**UART**), **I²C** ou **Modbus** e requer uma alimentação **VCC** externa de **5V a 14V**.

### Imagem ilustrativa do sensor K33:

![k33sensair](https://github.com/user-attachments/assets/aa34b2b5-d82e-4bf5-a147-c3a4f0ddb6d5)

---

## Funcionamento

Diferente de sensores como o **AO2** e o **BME280**, o **K33** possui comunicação bidirecional. Isso significa que, além de enviar dados, ele também recebe comandos para executar operações específicas. Por exemplo:

- O sensor não transmite dados continuamente. É necessário enviar um comando para que ele realize a leitura e retorne os valores.

Para mais informações técnicas, consulte o [datasheet do K33](https://co2meters.com/Documentation/Datasheets/DS33-ICB-01.pdf).

---

## Calibração

O **K33** já possui comandos internos para calibração em dois modos principais:

1. **Calibração com Ar Fresco:**  
   Ajusta o sensor para medir níveis de CO₂ em condições atmosféricas padrão (**400 ppm**).

2. **Calibração com Zero (Nitrogênio):**  
   Define o ponto de referência para concentrações de CO₂ próximas a **0 ppm**.

Os passos para calibração estão detalhados no [datasheet do K33](https://co2meters.com/Documentation/Datasheets/DS33-ICB-01.pdf).

---

## Configuração no Raspberry Pi

Antes de utilizar o sensor, é necessário ativar a comunicação serial no Raspberry Pi:

1. Clique no ícone do Raspberry Pi (imagem de uma framboesa).
2. Navegue até **Preferências** → **Configuração do Raspberry Pi**.
3. Na aba **Interface**, ative a opção **Serial**.
4. Reinicie o Raspberry Pi para aplicar as configurações.

---

## Exemplo de Código

A seguir, um exemplo em Python para realizar a leitura do sensor **K33** via UART:

```python
import serial
import time

def le_sensor_CO2():
    try:
        # Configura a comunicação serial com o dispositivo
        ser = serial.Serial(
            port="/dev/ttyS0",     # Porta serial do Raspberry Pi
            baudrate=9600,
            timeout=0.5,
        )

        ser.flushInput()  # Limpa o buffer de entrada
        ser.write(b"\xFE\x44\x00\x08\x02\x9F\x25")  # Envia o comando para leitura
        time.sleep(0.5)   # Aguarda a resposta do sensor

        resp = ser.read(7)  # Lê a resposta de 7 bytes do sensor

        high = resp[3]
        low = resp[4]
        co2_bruto = (high * 256) + low
        co2 = co2_bruto * 10  # Ajusta o valor conforme especificação do sensor

    except serial.SerialException as e:
        print("Erro de comunicação com o sensor de CO2:", e)

    except serial.SerialTimeoutException:
        print("Timeout: Nenhum dado recebido do sensor de CO2 dentro do tempo limite.")

    finally:
        # Fecha a porta serial ao finalizar
        if 'ser' in locals() and ser.is_open:
            ser.close()

    return co2
```
## Interpretação dos Resultados

O valor retornado pela função `le_sensor_CO2()` representa a concentração de CO₂ em ppm (partes por milhão).

- **Condições normais de ar fresco:** O valor típico é de aproximadamente **400 ppm (0,04%)**.
- **Faixa aceitável:** Entre **400 e 600 ppm** para ambientes com boa ventilação.

Esse código permite integrar o **K33** com o Raspberry Pi de forma eficiente, fornecendo leituras confiáveis de CO₂ para diversas aplicações.
