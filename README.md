

## NeuroSync



# NeuroSync - Documentação do Projeto



## Integrantes

- RM: 560227

- RM: 559613  

- RM: 560992



## Sobre o Projeto

O NeuroSync é uma plataforma de monitoramento neurológico que utiliza sensores IoT para capturar sinais cerebrais em tempo real. A solução processa e armazena dados neurológicos na nuvem para análise médica e pesquisa.



## O que Foi Implementado



### Infraestrutura Azure

- 2 Máquinas Virtuais provisionadas na Azure

VM Linux Ubuntu Server com Node-RED e Mosquitto MQTT

VM Windows: Windows Server com API Java

 Todas as VMs no mesmo Resource Group e Rede Virtual



### Configuração de Rede

Network Security Group configurado com as portas:

&nbsp; - 22 (SSH - Linux)

&nbsp; - 3389 (RDP - Windows) 

&nbsp; - 1880 (Node-RED)

&nbsp; - 1883 (MQTT)

&nbsp; - 8080 (API Java)

&nbsp; - 1521 (Oracle Database)



### Software Instalado



#### VM Linux

 Mosquitto MQTT Broker

 Node-RED

 Node.js



#### VM Windows  

- Java SDK 17

- API Spring Boot (.jar)

- Conexão com Oracle Database



## 2. Arquitetura do Sistema



### Diagrama de Fluxo

```

┌─────────────────┐    ┌───────────────┐    ┌──────────────────┐

│   👤 Usuário    │────│    🌐 Internet   │────│  📡 IP Público   │

│    App Mobile   │    │               │    │     Azure       │

└─────────────────┘    └───────────────┘    └──────────────────┘

&nbsp;        │                       │                      │

&nbsp;        │ 1                     │                      │

&nbsp;        ▼                       │                      ▼

┌─────────────────┐    ┌───────────────┐    ┌──────────────────┐

│  🖥️ VM Windows   │    │   ⚡ Wokwi IoT  │    │   🐧 VM Linux    │

│   API Java      │◄───│   Sensores    │────│   Broker MQTT   │

│   Porta: 8080   │    │  Neurológicos │    │   Porta: 1883   │

└─────────────────┘    └───────────────┘    └──────────────────┘

&nbsp;        │ 4                                      │ 3

&nbsp;        ▼                                       ▼

┌─────────────────┐                    ┌──────────────────┐

│  🗄️ Banco Oracle │                    │   🔄 Node-RED    │

│    FIAP         │                    │   Porta: 1880    │

│   Porta: 1521   │                    └──────────────────┘

└─────────────────┘

```



### Fluxo de Dados Numerado:

1. 👤 → 🖥️ - App Mobile → API Java (Porta 8080)

2.⚡ → 🐧 - Wokwi IoT → Broker MQTT (Porta 1883)  

3. 🐧 → 🖥️ - Node-RED → API Java (Porta 8080)

4. 🖥️ → 🗄️- API Java → Banco Oracle (Porta 1521)



## Tecnologias Utilizadas

- Microsoft Azure

- Ubuntu Server 22.04

- Windows Server 2022

- Java 17

- Spring Boot

- Node-RED

- Mosquitto MQTT

- Oracle Database



## Links

- Vídeo Demonstração:https://youtu.be/yXd07_uP2nQ



---

FIAP - 2TDSPS - 2025

