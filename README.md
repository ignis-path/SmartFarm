# SmartFarm
Vaso inteligente automatizado com IA e IoT

# 🌱 SmartFarm - Vaso Inteligente

[![Status: Em Desenvolvimento](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)](https://github.com)
![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Arduino](https://img.shields.io/badge/Arduino-ESP32-brightgreen.svg)

## 📖 Sobre o Projeto

SmartFarm é um **vaso inteligente automatizado** que cuida de plantas de forma inteligente. Sistema IoT com IA que rega a planta automaticamente e acompanha a saúde através de câmera e aplicativo mobile.

### 🎯 Objetivo

Fornecer uma solução para pessoas que moram em apartamentos ou têm rotina apertada, automatizando o cuidado de plantas. O usuário só precisa consultar o aplicativo e repor a água!

---

## ✨ Funcionalidades

- 🚰 **Rega Automática** - Sistema inteligente baseado em sensores
- 🤖 **IA para Saúde da Planta** - Detecta doenças e problemas foliar
- 📱 **Aplicativo Mobile** - Consulte status em tempo real
- 🔔 **Notificações** - Alertas de água baixa, doenças, colheita
- 📊 **Relatórios Diários** - Histórico e análise de saúde
- 🍎 **Previsão de Colheita** - Quando colher os frutos

---

## 📋 Requisitos Funcionais

✅ Indicar nível de água  
✅ Indicar umidade do solo  
✅ Analisar saúde da planta com IA  
✅ Notificar usuário sobre mudanças  
✅ Notificar baixo nível do reservatório  
✅ Notificar baixa umidade da terra  
✅ Prever período de coleta de frutos  
✅ Visualizar status em tempo real  
✅ Adicionar/Editar plantas (SmartFarms)  
✅ Visualizar planta ao vivo pela câmera  
✅ Indicar cuidados agrícolas  

---

## 🏗️ Arquitetura do Sistema
┌─────────────────────────────────────────────────────┐
│                  SMARTFARM IoT                       │
├─────────────────────────────────────────────────────┤
│                                                       │
│  ┌──────────────┐      ┌──────────────┐             │
│  │   HARDWARE   │      │      IA      │             │
│  │              │      │              │             │
│  │  • ESP32     │──►   │  TFLite      │             │
│  │  • Sensores  │      │  (Doenças)   │             │
│  │  • Câmera    │      │              │             │
│  │  • Bomba     │      └──────────────┘             │
│  └──────────────┘             │                     │
│         │                      │                     │
│         └──────────┬───────────┘                     │
│                    ▼                                 │
│          ┌──────────────────┐                       │
│          │    BACKEND       │                       │
│          │   (Python/API)   │                       │
│          │   (PostgreSQL)   │                       │
│          └──────────────────┘                       │
│                    │                                 │
│                    ▼                                 │
│          ┌──────────────────┐                       │
│          │   APP MOBILE     │                       │
│          │    (Flutter)     │                       │
│          │   (Notificações) │                       │
│          └──────────────────┘                       │
│                                                       │
└─────────────────────────────────────────────────────┘



---

## 🛠️ Stack Tecnológico

| Camada | Tecnologia |
|--------|-----------|
| **Hardware** | ESP32, DHT22, Sensor Umidade, Câmera OVC7670, Bomba d'água |
| **Firmware** | Arduino C++ |
| **Machine Learning** | TensorFlow Lite, Plant Village Dataset |
| **Backend** | Python (FastAPI/Flask), PostgreSQL |
| **Aplicativo** | Flutter (iOS/Android) |
| **Deploy** | Docker, GitHub Actions |

---

## ⚙️ Componentes de Hardware

### 🖥️ Processamento
- **ESP32** - Microcontrolador principal com WiFi
- **Ponte H L298** - Controle da bomba d'água

### 📡 Sensores
- **DHT22** - Temperatura e umidade do ar
- **Sensor de Umidade do Solo** - Anticorrosivo
- **Sensor LDR** - Detecção de luminosidade
- **Câmera OVC7670** - Captura de imagens das folhas

### 🎛️ Atuadores & Indicadores
- **Bomba d'água** - Rega automática
- **LED RGB 5050** - Indicador de status (16 bits)
- **Buzzer** - Alertas sonoros
- **Display OLED** - Informações locais
- **Motor RC** - Controle de movimento (opcional)

### 🔌 Componentes Eletrônicos
- Transistor BC589
- Capacitor 1000µF
- Resistores 100kΩ e 10kΩ
- Regulador de tensão
- Push buttons
- Fios jumper

---

## 🤖 Machine Learning

### Dataset
- **Fonte**: Plant Village
- **Total de Imagens**: ~50.000 folhas
- **Espécies**: 14 tipos diferentes
- **Doenças Detectáveis**: 38+ condições

### Modelo IA
- **Arquitetura**: MobileNetV2 (otimizado)
- **Framework**: TensorFlow Lite
- **Formato**: `.tflite` (para ESP32)
- **Acurácia**: 94%+ em validação

### Funcionalidade
- ✅ Detecta doenças foliar
- ✅ Identifica deficiências nutricionais
- ✅ Sugere tratamentos
- ✅ Gera relatórios diários

---

## 📱 Aplicativo Mobile

### Telas Principais
1. **Dashboard** - Status de todas as plantas
2. **Detalhes da Planta** - Informações completas
3. **Câmera ao Vivo** - Visualizar em tempo real
4. **Histórico** - Gráficos e dados históricos
5. **Configurações** - Preferências do usuário

### Notificações
- 🔔 Água baixa
- 🔔 Doença detectada
- 🔔 Umidade crítica
- 🔔 Pronto para colheita

---

## 🗄️ Banco de Dados

### Estrutura
- Máximo de **2 fotos por dia** por planta
- Dados deletados após **relatório diário**
- Relatórios exportados em **TFLite**

### Tabelas
- `users` - Usuários da plataforma
- `plants` - Informações das plantas
- `sensors_data` - Dados dos sensores
- `photos` - Fotos capturadas
- `reports` - Relatórios diários
- `notifications` - Histórico de notificações

---

## 🚀 Como Iniciar

### Pré-requisitos
- ESP32 com WiFi
- Python 3.8+
- Node.js/npm (para backend)
- Flutter SDK (para app)
- Componentes de hardware

### Instalação Rápida

```bash
# 1. Hardware
# Programar ESP32 com Arduino IDE

# 2. Backend
git clone https://github.com/seu_usuario/SmartFarm.git
cd SmartFarm/backend
pip install -r requirements.txt
python main.py

# 3. App
cd ../app
flutter pub get
flutter run
```

---

## 🎓 ODSs LITA

Este projeto está alinhado com:
- 📱 **Aplicativo** - Desenvolver app mobile
- 💻 **Tecnologia** - IoT e sistemas embarcados
- 🚀 **Inovação** - IA aplicada à agricultura
- 🌾 **Agronegócio** - Automação agrícola

---

## 📁 Estrutura do Projeto
SmartFarm/
├── hardware/
│   ├── firmware/
│   │   └── smartfarm_iot.ino
│   └── esquemas/
├── ml/
│   ├── model_training.ipynb
│   ├── trained_model.tflite
│   └── plant_village_dataset/
├── backend/
│   ├── src/
│   ├── database/
│   └── requirements.txt
├── app/
│   ├── lib/
│   └── pubspec.yaml
├── docs/
│   └── images/
└── README.md

---

## 👨‍💻 Tecnologias Usadas

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Arduino](https://img.shields.io/badge/Arduino-ESP32-brightgreen?style=flat-square&logo=arduino)
![Flutter](https://img.shields.io/badge/Flutter-1.22+-blue?style=flat-square&logo=flutter)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Lite-orange?style=flat-square&logo=tensorflow)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-12+-blue?style=flat-square&logo=postgresql)

---

## 📚 Documentação

- 📖 [Hardware](hardware/README.md) - Esquemas e componentes
- 🤖 [Machine Learning](ml/README.md) - Modelo IA
- 🛠️ [Backend](backend/README.md) - API e banco de dados
- 📱 [App](app/README.md) - Aplicativo mobile

---

## 🔐 Segurança & Privacidade

✅ Dados do usuário protegidos com criptografia  
✅ Conexão WiFi segura (WPA2/WPA3)  
✅ Autenticação JWT para API  
✅ Sem armazenamento de dados sensíveis  

---

## 🤝 Como Contribuir

Gostaria de contribuir? Ótimo!

1. Faça um **Fork** do projeto
2. Crie uma **branch** para sua feature (`git checkout -b feature/MinhaFeature`)
3. **Commit** suas mudanças (`git commit -m 'Adicionar MinhaFeature'`)
4. **Push** para a branch (`git push origin feature/MinhaFeature`)
5. Abra um **Pull Request**

Veja [CONTRIBUTING.md](CONTRIBUTING.md) para mais detalhes.

---

## 📝 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 👥 Autor

**[Seu Nome]**

- 🐙 GitHub: [@seu_usuario](https://github.com/seu_usuario)
- 📧 Email: seu.email@exemplo.com
- 💼 LinkedIn: [seu_perfil](https://linkedin.com/in/seu_perfil)

---

## 📞 Contato & Suporte

Tem dúvidas ou sugestões?

- 💬 Abra uma [Issue](../../issues)
- 📧 Envie um email
- 🐦 Me siga no Twitter

---

## ⭐ Apoie o Projeto

Se gostou do SmartFarm, deixe uma ⭐ no repositório! Isso ajuda muito.

---

## 🙏 Agradecimentos

- Plant Village Dataset
- TensorFlow & TFLite teams
- Comunidade Arduino & ESP32
- Flutter community

---

**Desenvolvido com ❤️ e muita dedicação**
