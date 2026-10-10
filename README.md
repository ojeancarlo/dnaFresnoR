# 🤘 Decodificando a Fresno: O DNA do novo age do Emocore

[![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Quarto-447099?style=for-the-badge&logo=quarto&logoColor=white)](https://quarto.org/)
[![reveal.js](https://img.shields.io/badge/reveal.js-E44D26?style=for-the-badge&logo=reveal.js&logoColor=white)](https://revealjs.com/)
[![Spotify API](https://img.shields.io/badge/Spotify_API-1DB954?style=for-the-badge&logo=spotify&logoColor=white)](https://developer.spotify.com/)

Um projeto de **storytelling com dados** que mapeia a evolução sonora e a constância estilística da banda **Fresno** ao longo de duas décadas. Utilizando dados de áudio extraídos do Spotify, a análise traduz atributos musicais (Energia, Valência, BPM, Dançabilidade) em explorações matemáticas para explicar o fenômeno do **"novo auge"** vivido por um dos pioneiros do emocore brasileiro.

A aplicação foi construída com um fluxo focado na **reprodutibilidade** e no poder visual das ferramentas tradicionais: a exploração, o cálculo estatístico e os cruzamentos descritivos foram realizados em **R**. Toda a apresentação foi desenhada, renderizada e unificada no ecossistema do **Quarto** (usando `reveal.js`), provando que é possível unir rigor analítico, controle criativo e escalabilidade através de código.

---

## 🔗 Links

- 🌐 **[Acesse a apresentação interativa no GitHub Pages](https://ojeancarlo.github.io/fresno-spotify-analysis/)**
- 📖 **[Leia o artigo completo sobre os bastidores analíticos no Medium](https://medium.com/@ojeancarlo/artigo-fresno)**
  <!-- TODO: substituir pelo link real do artigo -->

---

## 📑 Sumário

- [Funcionalidades e itens técnicos](#️-funcionalidades-e-itens-técnicos)
- [Tecnologias utilizadas](#-tecnologias-utilizadas)
- [Estrutura do projeto](#-estrutura-do-projeto)
- [Nota sobre reprodução local](#️-nota-sobre-reprodução-local)
- [Como executar localmente](#-como-executar-localmente)

---

## 🛠️ Funcionalidades e itens técnicos

### 1. Coleta via API e ETL
Extração de *audio features* das faixas e metadados de álbuns de toda a discografia da banda utilizando o pacote `spotifyr`, com tratamento, filtragem temporal e organização via `tidyverse` e `lubridate`.

### 2. Construção de features
- Criação de variáveis categóricas para agrupar as faixas em **eras musicais**: *Origem*, *Consolidação*, *Renovação* e *Novo Auge*.
- Cálculo do coeficiente de **"Polaridade Emo"**, combinando Energia e Valência.
- Extração matemática dos **centroides acústicos** de cada fase da banda.

### 3. Visualização customizada em R
Criação e aplicação de um tema customizado do zero no `ggplot2` (`tema_fresno()`), que injeta paleta de cores, tipografia e grids nas renderizações, evitando retrabalho visual de dezenas de linhas de código.

### 4. Storytelling de dados
- **Boxplots com jitter** (`geom_boxplot` + `geom_jitter`) para atestar a constância da duração e da volumetria das faixas ao longo dos anos.
- **Mapa emocional** com os 4 quadrantes da discografia, usando `geom_point` e os centroides de cada álbum.
- **Gráficos de densidade** (`geom_violin`) comprovando o pico de Dançabilidade nas eras de retomada recente da banda.
- **Heatmap de DNA Sonoro** (construído com pivoteamento dinâmico via `tidyr`), atestando a inabalável consistência rítmica do trio de Porto Alegre.

### 5. UI/UX documental
Interface construída com HTML e CSS nativos encapsulados em Quarto/Markdown, entregando:
- Cartões com dicas de leitura interativas;
- Carrossel infinito da trajetória de álbuns em CSS Animation;
- Dicionário de variáveis com design de *tiles* em grid;
- Rodapé giratório temático (vinil em CSS);
- Apresentação completamente fluida em `reveal.js`.

---

## 💻 Tecnologias utilizadas

| Categoria | Ferramentas |
|---|---|
| **Linguagens** | R, HTML, CSS |
| **Manipulação de dados (R)** | `dplyr`, `tidyr`, `lubridate`, `stringr`, `janitor` |
| **Importação e comunicação (R)** | `spotifyr` (coleta na API), `readxl`, `readr` |
| **Visualização de dados (R)** | `ggplot2`, `gghighlight`, `ggrepel`, `scales`, `kableExtra` |
| **Renderização visual** | Quarto (`revealjs`) |

---

## 📁 Estrutura do projeto

```text
fresno-spotify-analysis/
├── dados/ # Bases consolidadas em .rds (coletadas em 2022)
├── fresnoR.qmd # Código-fonte da apresentação (Quarto + reveal.js)
├── docs/ # Apresentação renderizada
└── *.Rproj # Projeto do RStudio
```

---

## ⚠️ Nota sobre reprodução local

Este projeto utilizou bases coletadas em **2022** (armazenadas na pasta `/dados/`) por meio da API do Spotify, através do pacote [`{spotifyr}`](https://github.com/charlie86/spotifyr).

Para quem deseja clonar e rodar o projeto hoje: o Spotify restringiu fortemente o acesso público de sua API a certas *audio features* cruciais (como **Valência** e **Acústica**), que embasam esta apresentação. Por esse motivo, as bases consolidadas foram deixadas em arquivos **`.rds` estáticos**. Assim, você consegue renderizar a apresentação localmente de forma limpa, **sem depender da API**.

---

## 🚀 Como executar localmente

**1. Clone este repositório:**

```bash
git clone https://github.com/ojeancarlo/fresno-spotify-analysis.git
```

**2. Abra o arquivo do projeto (`.Rproj`) no RStudio.**

**3. Instale as dependências** (caso ainda não as tenha):

```r
install.packages(c(
  "tidyverse", "lubridate", "janitor", "readxl", "readr",
  "gghighlight", "ggrepel", "scales", "kableExtra"
))
```

**4. Clique em `Render` no arquivo `fresnoR.qmd`.** O RStudio se encarregará de ler as bases estáticas e gerar o seu `index.html`.

---

## Feito por **[Jean Carlo](https://github.com/ojeancarlo)**.
