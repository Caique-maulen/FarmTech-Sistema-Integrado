# 🌱 FarmTech Solutions - Sistema Integrado (Fase 7)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-red.svg)
![ML](https://img.shields.io/badge/ML-Random%20Forest-orange.svg)
![YOLO](https://img.shields.io/badge/YOLO-v5-yellow.svg)
![Status](https://img.shields.io/badge/Status-Completo-success.svg)

## 📖 Sobre o Projeto

**FarmTech Solutions Fase 7** é um **dashboard integrado único** que consolida todas as tecnologias desenvolvidas nas Fases 1-6 do projeto acadêmico FIAP em uma **interface web moderna e interativa**.

### 🎯 Objetivo Principal

Criar um **sistema único acessível via navegador** onde o usuário pode:
- 🌾 Gerenciar culturas e calcular áreas de plantio
- 🔌 Monitorar sensores IoT em tempo real
- 🤖 Fazer predições com Machine Learning
- 👁️ Detectar objetos com visão computacional

**Tudo em um só lugar!** Sem precisar executar múltiplos programas ou navegar por diferentes pastas.

---

## 🏗️ Arquitetura do Sistema

```
┌─────────────────────────────────────────────────────┐
│         STREAMLIT DASHBOARD (Navegador Web)         │
│                   http://localhost:8501             │
└────────────────────┬────────────────────────────────┘
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
┌──────────────┐ ┌──────────┐ ┌──────────┐
│   Página 1   │ │ Página 2 │ │ Página 3 │
│ Agricultura  │ │   IoT    │ │    ML    │
└──────────────┘ └──────────┘ └──────────┘
                     ▼
              ┌──────────────┐
              │   Página 4   │
              │    Visão     │
              └──────────────┘
                     │
                     ▼
              ┌──────────────┐
              │   Database   │
              │    SQLite    │
              └──────────────┘
```

---

## 📁 Estrutura do Projeto

```
farmtech_integrado/
│
├── 📄 app.py                         ⭐ DASHBOARD PRINCIPAL
│                                        Execute ESTE arquivo!
│
├── 📁 pages/                          Páginas do dashboard
│   ├── 1_🌾_Agricultura.py            Fase 1 integrada
│   ├── 2_🔌_IoT_Sensores.py           Fase 3 integrada
│   ├── 3_🤖_Machine_Learning.py       Fase 4 integrada
│   └── 4_👁️_Visao_Computacional.py    Fase 6 integrada
│
├── 📁 modules/                        Módulos reutilizáveis
│   ├── agricultura/
│   ├── iot/
│   ├── ml/
│   └── visao/
│
├── 📁 database/                       Banco de dados centralizado
│   ├── schema.sql                     Estrutura do banco
│   └── farmtech.db                    Banco SQLite (criado automaticamente)
│
├── 📁 models/                         Modelos de ML e YOLO
│   └── irrigation_model.pkl           Modelo Random Forest
│
├── 📁 data/                           Dados de treinamento
│   └── training_data.csv
│
├── 📁 assets/                         Imagens e recursos
│
├── 📁 utils/                          Utilitários
│
├── 📄 requirements.txt                Dependências Python
└── 📄 README.md                       Este arquivo
```

---

## 🚀 Como Usar o Sistema

### 📋 Pré-requisitos

- **Python 3.8 ou superior**
- **Navegador web** (Chrome, Firefox, Edge, Safari)

### 1️⃣ Instalação

```bash
# 1. Navegue até a pasta do projeto
cd farmtech_integrado

# 2. (Opcional mas recomendado) Crie um ambiente virtual
python -m venv venv

# 3. Ative o ambiente virtual
# No Windows:
venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate

# 4. Instale as dependências
pip install -r requirements.txt
```

### 2️⃣ Executar o Dashboard

```bash
# Execute o dashboard
streamlit run app.py
```

O dashboard será aberto automaticamente no seu navegador em: **http://localhost:8501**

### 3️⃣ Navegação

Use o **menu lateral** (sidebar à esquerda) para navegar entre as páginas:

1. **🏠 Home** - Página principal (app.py)
2. **🌾 Agricultura** - Gestão de culturas e cálculo de áreas
3. **🔌 IoT Sensores** - Monitoramento de sensores ESP32
4. **🤖 Machine Learning** - Predições de irrigação
5. **👁️ Visão Computacional** - Detecção de objetos com YOLO

---

## 🎮 Funcionalidades por Página

### 🏠 Página Inicial (app.py)

**O que faz:**
- Apresenta visão geral do sistema
- Mostra métricas principais
- Explica cada fase do projeto
- Links rápidos para documentação

**Como usar:**
- Apenas acesse - é a página inicial!

---

### 🌾 Agricultura Digital (Fase 1)

**Funcionalidades:**
- ✅ Calcular áreas de plantio
  - Café: ruas retangulares
  - Soja: talhões quadrados
- ✅ Cadastrar culturas
- ✅ Gerenciar insumos
- ✅ Exportar dados para CSV

**Como usar:**
1. Acesse a página "🌾 Agricultura" no menu lateral
2. Use a aba "Cálculo de Áreas" para calcular áreas
3. Use a aba "Gestão de Culturas" para cadastrar culturas
4. Use a aba "Gestão de Insumos" para calcular quantidades necessárias

**Dados armazenados:**
- Session state (temporário, dura enquanto a sessão estiver ativa)

---

### 🔌 Monitoramento IoT (Fase 3)

**Funcionalidades:**
- ✅ Visualizar dados de sensores em tempo real
- ✅ Simulador de leituras (não requer hardware)
- ✅ Gráficos de tendências
- ✅ Controle manual da bomba
- ✅ Histórico de medições
- ✅ Exportar dados para CSV

**Como usar:**
1. Acesse a página "🔌 IoT Sensores"
2. Use o botão "Gerar Nova Leitura" na sidebar para simular dados
3. Visualize métricas em tempo real
4. Veja gráficos de tendências nas abas

**Lógica de Irrigação:**
```python
Irrigar = (Umidade < 40%) AND (P_deficiente OR K_deficiente)
```

**Dados armazenados:**
- SQLite: `database/farmtech.db`
- Tabela: `leituras`

**Hardware (opcional):**
- Conecte ESP32 via serial para dados reais
- Modo simulador funciona sem hardware

---

### 🤖 Machine Learning (Fase 4)

**Funcionalidades:**
- ✅ Treinar modelo Random Forest
- ✅ Fazer predições de irrigação
- ✅ Analisar importância de features
- ✅ Visualizar métricas de performance
- ✅ Histórico de predições

**Como usar:**
1. Acesse "🤖 Machine Learning"
2. **Aba "Treinamento":**
   - Gere dados de treinamento
   - Clique em "Treinar Modelo"
3. **Aba "Predições":**
   - Configure parâmetros (umidade, pH, P, K)
   - Clique em "Fazer Predição"
4. **Abas "Análise" e "Performance":**
   - Veja métricas do modelo

**Modelo:**
- Algoritmo: Random Forest Classifier
- Features: umidade, pH, fósforo (P), potássio (K)
- Target: irrigar (0/1)
- Acurácia esperada: ~100% (dados sintéticos)

**Dados armazenados:**
- Modelo: `models/irrigation_model.pkl`
- Dados: `data/training_data.csv`

---

### 👁️ Visão Computacional (Fase 6)

**Funcionalidades:**
- ✅ Upload de imagens
- ✅ Detecção com YOLOv5
- ✅ Visualização de resultados
- ✅ Histórico de detecções
- ✅ Exportar resultados

**Como usar:**
1. Acesse "👁️ Visão Computacional"
2. **Aba "Upload & Detecção":**
   - Faça upload de uma imagem (JPG, PNG)
   - Configure parâmetros
   - Clique em "Executar Detecção"
3. **Aba "Resultados":**
   - Veja histórico de todas as detecções
   - Gráficos de distribuição

**Modelos disponíveis:**
- YOLOv5s (rápido)
- YOLOv5m (balanceado)
- YOLOv5l (preciso)

**Nota:** Se YOLOv5 não estiver instalado, funciona em modo demonstração.

**Dados armazenados:**
- Imagens: `assets/`
- Session state (histórico temporário)

---

## 💾 Banco de Dados (Fase 2)

### Estrutura

O sistema usa **SQLite** como banco de dados centralizado.

**Localização:** `database/farmtech.db`

**Tabelas principais:**
- `leituras` - Dados dos sensores IoT

**Schema SQL:** `database/schema.sql`

### Como acessar o banco

```bash
# Via linha de comando
sqlite3 database/farmtech.db

# Ou use ferramentas GUI:
# - DB Browser for SQLite (recomendado)
# - DBeaver
# - SQLiteStudio
```

---

## 🔧 Troubleshooting

### Problema: "ModuleNotFoundError: No module named 'streamlit'"

**Solução:**
```bash
pip install streamlit
# ou
pip install -r requirements.txt
```

### Problema: "YOLOv5 não está instalado"

**Solução:**
```bash
pip install ultralytics opencv-python pillow
```

**Nota:** O sistema funciona em modo demonstração sem YOLO.

### Problema: "Address already in use"

**Solução:**
```bash
# Use outra porta
streamlit run app.py --server.port 8502
```

### Problema: Dashboard não abre no navegador

**Solução:**
```bash
# Abra manualmente
# URL: http://localhost:8501
```

### Problema: Erro no treinamento do modelo ML

**Solução:**
```bash
# Certifique-se de que scikit-learn está instalado
pip install scikit-learn numpy pandas
```

---

## 📊 Dados de Teste

### Para IoT (Sensores)

Clique em "Gerar Nova Leitura" na sidebar - dados simulados serão criados automaticamente.

### Para ML (Machine Learning)

Clique em "Gerar Dados de Treinamento" na aba Treinamento - 1000 amostras sintéticas serão criadas.

### Para Visão (YOLO)

Faça upload de qualquer imagem JPG/PNG. Exemplos de imagens para teste:
- Fotos de plantas
- Fotos de folhas
- Fotos de lavouras

---

## 🎯 Diferenciais do Sistema Integrado

### ✅ O que torna este sistema especial:

1. **Interface Única** - Tudo acessível via navegador web
2. **Navegação Simples** - Menu lateral intuitivo
3. **Sem Instalação de Banco** - SQLite funciona out-of-the-box
4. **Modo Demonstração** - Funciona sem hardware ou YOLO
5. **Exportação de Dados** - CSV em todas as páginas
6. **Visualizações Interativas** - Gráficos com Plotly
7. **Responsivo** - Funciona em desktop e mobile

### 🔄 Fluxo de Dados Integrado

```
Sensores (Fase 3)
        ↓
   SQLite Database (Fase 2)
        ↓
   Dashboard Streamlit
        ↓
   Machine Learning (Fase 4)
        ↓
    Predições
```

---

## 📚 Documentação Adicional

### Streamlit

- [Documentação Oficial](https://docs.streamlit.io/)
- [Galeria de Componentes](https://streamlit.io/components)

### Machine Learning

- [Scikit-learn](https://scikit-learn.org/)
- [Random Forest](https://scikit-learn.org/stable/modules/ensemble.html#forest)

### Visão Computacional

- [YOLOv5](https://github.com/ultralytics/yolov5)
- [Ultralytics Docs](https://docs.ultralytics.com/)

---

## 🎓 Conceitos Aplicados (Fase 7)

### Tecnologias Integradas:

- ✅ **Python** - Linguagem principal
- ✅ **Streamlit** - Framework de dashboard
- ✅ **SQLite** - Banco de dados
- ✅ **Pandas** - Manipulação de dados
- ✅ **Scikit-learn** - Machine Learning
- ✅ **Plotly** - Visualizações interativas
- ✅ **YOLOv5** - Deep Learning
- ✅ **OpenCV** - Processamento de imagens

### Conceitos de Engenharia:

- ✅ **Arquitetura Modular** - Separação em páginas
- ✅ **Reutilização de Código** - Módulos compartilhados
- ✅ **Estado Persistente** - Session state e banco de dados
- ✅ **Interface Responsiva** - Layout adaptativo
- ✅ **Separação de Responsabilidades** - Cada página uma função

---

## 🏆 Checklist de Entrega (Fase 7)

- [x] ✅ Dashboard único em Streamlit
- [x] ✅ Integração da Fase 1 (Agricultura)
- [x] ✅ Integração da Fase 2 (Banco de Dados)
- [x] ✅ Integração da Fase 3 (IoT/ESP32)
- [x] ✅ Integração da Fase 4 (ML)
- [x] ✅ Integração da Fase 6 (Visão)
- [x] ✅ Navegação por menu/botões
- [x] ✅ Tudo em uma única pasta de projeto
- [x] ✅ Documentação completa (README)
- [x] ✅ Requirements.txt
- [x] ✅ Sistema 100% funcional

---

## 🎬 Como Demonstrar o Projeto

### Roteiro de Apresentação (10-15 min):

1. **Introdução (2 min)**
   - Mostre a página inicial
   - Explique a integração das fases

2. **Agricultura (2 min)**
   - Calcule uma área de café
   - Cadastre uma cultura

3. **IoT (3 min)**
   - Gere algumas leituras simuladas
   - Mostre gráficos de tendências
   - Explique a lógica de irrigação

4. **Machine Learning (3 min)**
   - Treine o modelo (se não estiver treinado)
   - Faça uma predição
   - Mostre análise de importância

5. **Visão (3 min)**
   - Faça upload de uma imagem
   - Execute detecção
   - Mostre resultados

6. **Conclusão (2 min)**
   - Recapitule integração
   - Mostre banco de dados
   - Destaque diferenciais

---

## 🆘 Suporte

### Problemas Comuns

1. **Erro ao importar módulo** → `pip install [módulo]`
2. **Porta em uso** → Use `--server.port 8502`
3. **Banco não cria** → Permissões da pasta `database/`
4. **YOLO não funciona** → Use modo demonstração

---

## 👥 Equipe

**Projeto Acadêmico - FIAP**
- Fase 7 - Capítulo 1
- Sistema Integrado de Agricultura Inteligente
- Ano: 2025

---

## 📜 Licença

Este projeto foi desenvolvido para fins educacionais como parte do curso da **FIAP**.

---

<div align="center">

## 🌱 FarmTech Solutions - Fase 7

**Sistema Integrado de Agricultura Inteligente**

*Cultivando o futuro com tecnologia!* 🚜

---

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

</div>
