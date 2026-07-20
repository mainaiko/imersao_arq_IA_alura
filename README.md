# Alura Album - Copa do Mundo Tech

## Objetivo
O projeto é um álbum de figurinhas virtual e interativo ("Alura Album - Copa do Mundo Tech"). O álbum celebra os pioneiros, gigantes e arquitetos de diferentes áreas da tecnologia, separando-os por categorias como Inteligência Artificial, Python e Bancos de Dados. O projeto foca em entregar uma experiência web premium e dinâmica, apresentando uma interface rica, com efeitos tridimensionais de virada de página (flip-book), arrasto interativo das páginas pelo usuário e uma identidade visual moderna e tecnológica.

## Arquivos do Projeto e suas Funcionalidades

### `index.html`
Este é o arquivo principal que estrutura a aplicação e define seu conteúdo. Suas responsabilidades incluem:
- Definição da estrutura do DOM para o layout principal e controles de interface (botões de som e setas de navegação).
- Criação e ordenação das páginas do álbum (capa, páginas temáticas, etc.), já estruturadas para suportar o efeito tridimensional de "flip-book".
- Definição dos *slots* individuais onde cada figurinha será alocada.
- Importação de bibliotecas externas de fontes (Google Fonts: Inter e Outfit).

### `app.js`
Este arquivo contém toda a lógica de negócio e interatividade no lado do cliente (frontend). Suas funcionalidades abrangem:
- **Consumo de API:** Realiza requisições assíncronas para um backend local (`http://localhost:8000/figurinhas`) para resgatar os dados das figurinhas e preencher de forma dinâmica os espaços no álbum (`index.html`).
- **Animação de Virada de Página:** Configura e inicializa o componente `St.PageFlip`, que simula a física de um livro real sendo folheado.
- **Eventos de Arraste (Drag):** Monitora eventos de clique, toque e movimento do mouse para permitir que o usuário arraste os cantos das páginas livremente.
- **Gerenciamento de Estado UI:** Controla os comportamentos visuais dos botões da interface, como os botões de próxima página/página anterior e alternância de efeitos sonoros.

### `style.css`
O arquivo de folhas de estilo é responsável pela estética premium e futurista do projeto. Suas atribuições são:
- **Design System:** Define um conjunto de variáveis globais de cor (tons de azul e preto profundos) para assegurar uma paleta consistente.
- **Estilização Layout:** Define o visual do álbum (tamanhos de página, sombras simulando lombadas de livro, cursores personalizados de interação).
- **Identidade Visual:** Aplica gradientes radiais sofisticados de plano de fundo e cria o design elegante dos emblemas (*badges*) para as categorias.
- **Transições:** Aplica animações e efeitos suaves (micro-interações) nos botões de controle para melhorar a experiência geral do usuário.

### `back_end/main/main.py`
Este é o coração do nosso servidor backend, construído utilizando Python e **FastAPI**. Ele é a API que alimenta o álbum com os dados e imagens das figurinhas. Suas principais partes são:
- **Configuração de CORS:** Utiliza o `CORSMiddleware` para aceitar requisições de qualquer origem (inclusive do Live Server do frontend rodando em outra porta).
- **Banco de Dados em Memória:** Contém uma lista estática de dicionários com as 30 figurinhas oficiais da "Copa do Mundo Tech" (incluindo `id`, `nome`, `categoria` e o `imagem_url`).
- **Endpoint GET `/figurinhas`:** Retorna a lista completa de figurinhas disponíveis em formato JSON.
- **Endpoint Dinâmico GET `/figurinhas/{id}/imagem`:** Recebe um `id` numérico, e utiliza a biblioteca `glob` para buscar automaticamente dentro da pasta `figurinhas/` qual é o arquivo de imagem correspondente (usando o prefixo, ex: `01`, não importando a extensão da imagem). Caso encontrado, ele entrega o arquivo bruto via `FileResponse`. Retorna erro 404 se a imagem não existir.

---

## Como Executar o Projeto Localmente

Se você deseja rodar este projeto e testar a comunicação entre o Frontend e a API, siga os passos abaixo no seu terminal:

### 1. Preparando o Backend (API)
Primeiro, garanta que você tem o Python instalado na sua máquina.

Crie um ambiente virtual (recomendado) na raiz do projeto:
```bash
python3 -m venv .venv
```

Ative o ambiente virtual:
- No **Linux ou macOS**:
  ```bash
  source .venv/bin/activate
  ```
- No **Windows**:
  ```powershell
  .venv\Scripts\activate
  ```

Instale as dependências usando o arquivo `requirements.txt`:
```bash
pip install -r requirements.txt
```

Navegue até a pasta do servidor e inicie a API:
```bash
cd back_end/main
uvicorn main:app --reload
```
A API agora estará rodando em: `http://localhost:8000`.

### 2. Rodando o Frontend
Com o backend já rodando, você pode iniciar o frontend de diferentes maneiras. A mais comum é:
- Utilizar a extensão **Live Server** no VS Code: basta abrir o arquivo `index.html` e clicar em "Go Live".
- Ou, no terminal, abra uma nova aba na raiz do projeto e rode o servidor nativo do Python:
```bash
python3 -m http.server 5500
```
Acesse `http://localhost:5500` no seu navegador e você verá o álbum interativo ganhando vida e buscando as imagens diretamente da sua API!
