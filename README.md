# WebGIS — Planos Diretores do Brasil

Plataforma **WebGIS Nacional** do Projeto **Planos Diretores do Brasil**, construída no padrão **Geoportal** (React + TypeScript + Vite + MapLibre GL JS + Tailwind CSS) com backend unificado em **FastAPI**, extração documental (PDF/OCR) e assistente de **Inteligência Artificial (RAG)** para interpretação didática e técnica da legislação urbanística e ambiental brasileira.

- **Repositório irmão (Plugin QGIS):** https://github.com/eriksdhoffmann/Plugin-Plano-Diretor
- **Geoportal publicado (GitHub Pages):** https://eriksdhoffmann.github.io/Plano-Diretor-WebGis/

## Funcionalidades Principais

- **Panorama Nacional (5.571 municípios IBGE):** mapa interativo das 27 UFs e dos municípios brasileiros integrado à base oficial **IBGE MUNIC 2021** (identificando municípios com Plano Diretor, em elaboração e sem Plano Diretor), com exportação CSV.
- **Geoportal Municipal (padrão Itajaí / Araquari):** controle de camadas retrátil, legenda dinâmica preservando siglas e nomes locais, busca de logradouros, troca de mapa base (Fundo Limpo, OpenStreetMap, Satélite) e barra de coordenadas/escala.
- **Interpretador Didático do Plano Diretor:** guia interativo e cartões explicativos dentro do mapa para cada camada (*Sistema Viário*, *Zoneamento*, *Macrozoneamento*, *Perímetro Urbano*, *APP*, *Unidades de Conservação* e *Cota 40*).
- **Assistente de IA Fundamentado (RAG):** modos **Didático**, **Técnico** e **Técnico de Prefeitura** com 7 blocos rastreáveis, distinção ambiental obrigatória (Código Florestal — Lei nº 12.651/2012) e leitor/extrator de PDFs.
- **Modo Híbrido:** funciona 100% estático no navegador (GitHub Pages) e também conectado ao backend FastAPI local.

## Estrutura do Repositório

```text
Plano-Diretor-WebGis/
├── apps/webgis/             # Frontend React + TypeScript + MapLibre GL JS
├── backend/                 # API FastAPI + SQLAlchemy/PostGIS + Extrator PDF + IA RAG
├── data/                    # Base IBGE (5.571 municípios), IBGE MUNIC 2021, catálogo e legislações
├── scripts/                 # Coleta IBGE/MUNIC, validação de catálogo e bundle estático
├── docs/                    # Arquitetura, catálogo e rastreabilidade
├── tests/backend/           # Testes automatizados da API, RAG e extração documental
├── ABRIR_GEOPORTAL_PLANOS_DIRETORES.bat
└── docker-compose.yml       # Stack completa com PostgreSQL/PostGIS + FastAPI + WebGIS
```

## Execução Local Rápida

### Atalho Windows
Execute `ABRIR_GEOPORTAL_PLANOS_DIRETORES.bat` na raiz do projeto.

### Manualmente
1. **Backend FastAPI:**
   ```powershell
   cd backend
   python -m venv .venv
   .\.venv\Scripts\pip install -r requirements.txt
   cd ..
   .\backend\.venv\Scripts\python -m uvicorn backend.api.main:app --reload --port 8000
   ```
2. **Frontend WebGIS:**
   ```powershell
   cd apps/webgis
   npm install
   npm run dev
   ```
