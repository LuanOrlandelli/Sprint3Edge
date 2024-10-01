# Sprint 3 de Edge Computing e Computer Sistems

## Integrantes do Grupo
- **Luan Orlandelli** - 554747
- **Igor Medeiros** - 555337
- **Jorge Luiz** - 554418
- **Arthur Bobadilla** - 555056

- # Projeto IoT - Coleta de Dados com ESP32 e Servidor Linux

## Descrição do Projeto

Este projeto IoT tem como objetivo coletar dados ambientais utilizando sensores conectados a um ESP32 e enviá-los para um servidor rodando em uma máquina virtual Linux. Inicialmente, utilizamos um LDR (Light Dependent Resistor) para medir luminosidade e um DHT22 para medir temperatura e umidade. Esses dados são enviados via protocolo MQTT ao servidor, onde ficam disponíveis para consulta por outros dispositivos conectados.

No futuro, o projeto será expandido para integrar dados de telemetria relacionados à Fórmula E, exibindo-os em dashboards na aba "Dados" de nosso site da Sprint 3. Esse dashboard será utilizado para demonstrar a performance dos pilotos e carros no projeto TalentoE.

## Estrutura do Projeto

1. **Hardware Utilizado**:
   - ESP32
   - Sensor LDR
   - Sensor DHT22
   - Máquina Virtual Linux (servidor)

2. **Software**:
   - Protocolo de comunicação MQTT
   - Broker MQTT (e.g., Mosquitto)
   - Scripts Python para coleta e envio de dados no ESP32
   - Servidor MQTT na máquina virtual para recebimento e processamento de dados
   - Visualização de dados em dashboards (a ser integrado na Sprint final)

## Requisitos

### Hardware:
- ESP32
- Sensor LDR
- Sensor DHT22
- Máquina virtual Linux ou servidor físico
- Conexão Wi-Fi

### Software:
- Python 3.x
- Biblioteca `paho-mqtt` para Python
- MQTT Broker (Mosquitto recomendado)
- Ambiente de desenvolvimento para ESP32 (Arduino IDE ou PlatformIO)
- Servidor Linux configurado (preferencialmente Ubuntu 20.04)

## Instruções de Uso

### 1. Configuração da Máquina Virtual (Servidor IoT)

1. **Criar a Máquina Virtual**:
   - Utilizar qualquer plataforma de virtualização (VirtualBox, VMWare, etc.) para criar uma máquina virtual com Linux (Ubuntu recomendado).
   - Configurar o servidor com acesso à internet e permitir conexões via rede interna.

2. **Instalar o Broker MQTT**:
   ```bash
   sudo apt update
   sudo apt install mosquitto mosquitto-clients```
   -Iniciar o serviço
   ```sudo systemctl start mosquitto
   sudo systemctl enable mosquitto
3. **Configurar o Broker**:
   -Utilize o comando a seguir para verificar se o broker está funcionando:
   ```bash
   mosquitto_sub -h localhost -t "test"

### 2. Configuração do ESP32

1. **Intalar Biblioteca MQTT no ESP32**:
   -Se estiver utilizando o Arduino IDE:
   -Vá para Sketch -> Include Library -> Manage Libraries
   -Pesquise por ```PubSubClient``` e instale a biblioteca

2. **Escrever código para o ESP32**:
   -O ESP32 deverá ler os dados do LDR e do DHT22 e enviá-los ao servidor via MQTT

3. **Fazer Upload do Código para o ESP32**:
   -Após ajustar os parâmetros de rede e servidor, faça o upload do código no ESP32 usando Arduino IDE ou PlatformIO.


### 3. Visualização de Dados no Servidor

1. **Subscrição para Receber Dados:**:
  -No servidor Linux, utilize o seguinte comando para subscrever aos tópicos MQTT:
  ```mosquitto_sub -h localhost -t "sensor/temperatura"
  mosquitto_sub -h localhost -t "sensor/umidade"
2. **Dashboard de Visualização (Sprint Final):**:
  -Mais tarde, os dados serão integrados a um dashboard gráfico, acessível pela aba "Dados" no site da Sprint, utilizando bibliotecas como Chart.js ou D3.js para exibição visual.
