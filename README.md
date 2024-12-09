# Sistema computacional embarcado de análise de gases para controle de atmosfera em pós-colheita de frutas

Este projeto desenvolve um sistema computacional embarcado capaz de analisar e controlar os gases oxigênio (O₂) e dióxido de carbono (CO₂) de um ambiente, com foco na preservação de frutas em câmaras de atmosfera controlada. O sistema é projetado com viabilidade econômica, utilizando a plataforma Raspberry Pi e sensores avançados aplicados à agricultura de precisão, equilibrando eficiência tecnológica e otimização de recursos financeiros e operacionais.

---

## **Objetivo**

Criar um sistema que:
- Monitore e controle os níveis de O₂ e CO₂ em uma câmara de atmosfera controlada.
- Garanta a segurança elétrica e operacional utilizando componentes isoladores e confiáveis.
- Integre um sistema de automação com atuadores para controle dos gases no ambiente.

---

## **Componentes Utilizados**

### **Leitura e Análise dos Gases**
- **Plataforma Computacional**: Raspberry Pi 4 Model B
- **Sensores**:
  - **AO2 SENSOR Citicel** (Sensor de oxigênio - comunicação I²C)
  - **K33 SenseAir** (Sensor de dióxido de carbono - comunicação UART)
  - **BME280** (Sensor de pressão barométrica, umidade e temperatura)
- **Conversor e Isoladores**:
  - **ADS1115** (Conversor ADC)
  - **ISO1540** (Isolador capacitivo)
- **Display**:
  - **DWIN HDW070_008LZ02** (Display touch - comunicação USB serial)

**Esquema do hardware de sensores**  
![Hardware Sensores](eletrica-sensores.png)  
Os sensores comunicam-se diretamente com o Raspberry Pi. O ISO1540 garante a segurança isolando o sistema de surtos elétricos.  

---

### **Sistema Elétrico dos Atuadores**
- **Componentes**:
  - **PCF8574** (Expansor de I/O)
  - **Relé de estado sólido 220V**
  - **Eletroválvula pneumática 220V AC**
  - **Relé 5V**
  - **Bomba de ar a vácuo 5V**

**Esquema elétrico dos atuadores**  
![Sistema Elétrico](diagrama-eletrico.png)  
O Raspberry Pi envia comandos ao PCF8574 para definir os pinos de controle (0 ou 1), que acionam os relés responsáveis pelos atuadores, ativando ou desativando as eletroválvulas e a bomba de ar.

---

### **Bancada de Testes**

- **Componentes da Bancada**:
  - Engates rápidos e mangueiras para circulação de ar.
  - Dois tubos de PVC (100mm):
    - **Câmara**: onde ficam as frutas.
    - **Adsorvedor de CO₂**: preenchido com cal (substância adsorvedora de CO₂).
- **Entradas e Saídas**:
  - **In N2**: Entrada de nitrogênio, reduzindo os níveis de O₂ e CO₂.
  - **Out Ads**: Saída para o adsorvedor de CO₂.
  - **In Ads**: Retorno do ar processado pelo adsorvedor.
  - **Alívio**: Entrada/saída para alívio da pressão, admitindo oxigênio ou liberando excesso de nitrogênio.

**Diagrama da bancada de testes**  
![Bancada de Testes](diagrama-controle.png)

---

## **Documentação Complementar**

Para facilitar o entendimento e implementação do projeto, consulte os arquivos do repositório:

- [Instalação Raspberry Pi](Instalação%20Raspberry%20Pi.pdf): Guia inicial para configuração do Raspberry Pi.
- [AO2 Sensor](AO2%20Sensor.pdf): Guia para o sensor de oxigênio AO2.
- [K33 Sensor](K33%20Sensor.pdf): Guia para o sensor de CO₂ K33.
- [BME280 Sensor](BME280%20Sensor.pdf): Guia para o sensor de pressão, umidade e temperatura BME280.

---
![Diagrama-Controle](https://github.com/user-attachments/assets/62e59859-df30-46b5-98f7-e61c4e3deaf5)
![eletrica-sensores](https://github.com/user-attachments/assets/1c893533-5b0e-4878-96ec-fe9573768507)
![diagrama-eletrico](https://github.com/user-attachments/assets/185ea473-0847-44f3-9b5b-1522a99d31e8)
