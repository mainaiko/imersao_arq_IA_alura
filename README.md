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
