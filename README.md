# CineBusca — Descubra onde assistir

Aplicação web responsiva para explorar filmes, consultar provedores de streaming no Brasil e manter listas locais. A fonte de dados de filmes é a API v3 do TMDB; os dados de disponibilidade são fornecidos pelo TMDB/JustWatch.

## Requisitos

- Node.js LTS instalado (inclui npm)
- Uma chave de API v3 do TMDB
- Conexão com a internet

## 1. Configurar a chave

1. Crie uma conta em https://www.themoviedb.org/
2. Vá às configurações da conta > API e solicite acesso.
3. Na pasta do projeto, copie `.env.example` para `.env.local`.
4. Abra `.env.local` e substitua `COLOQUE_SUA_CHAVE_TMDB_AQUI` pela sua chave real.

No Windows CMD:
```bat
copy .env.example .env.local
notepad .env.local
```

## 2. Rodar localmente

Abra o terminal dentro da pasta do projeto:
```bash
npm install
npm run dev
```
Abra a URL que o Vite mostrar, normalmente http://localhost:5173.

## 3. Gerar os arquivos para publicação

```bash
npm install
npm run build
npm run preview
```

O site pronto será gerado na pasta `dist/`. Envie **o conteúdo de `dist/`** para uma hospedagem de site estático, como Netlify, Vercel ou GitHub Pages.

### Importante sobre a chave API

Este projeto inicial usa a chave no navegador por meio de `VITE_TMDB_API_KEY`. Qualquer chave incluída num build Vite pode ser vista no código entregue ao visitante. Não trate `.env.local` como segredo após publicar o site.

Para uma aplicação pública de produção, configure um backend/proxy (por exemplo, uma função serverless) que armazene a chave como variável de ambiente no servidor e encaminhe somente as rotas necessárias do TMDB. Depois altere a função `tmdb()` em `src/App.jsx` para usar seu endpoint `/api/tmdb` sem incluir `api_key` no navegador. Configure também limites de uso e cache para evitar abuso.

## Recursos incluídos

- Catálogo de filmes populares
- Pesquisa por título
- Página de detalhes com sinopse, nota, duração, gêneros, direção e elenco
- Provedores brasileiros, separados por assinatura, gratuito, anúncios, aluguel e compra quando o TMDB fornecer esses dados
- Filtros de gênero, ano, nota, ordenação e provedor
- Favoritos e lista “Quero assistir” no navegador
- Preferência de serviços e tema claro/escuro
- Layout adaptável para computador, tablet e celular
- Estados de carregamento, erros e listas vazias

## Limitações importantes

- Os dados e a disponibilidade dependem do TMDB e podem estar incompletos ou desatualizados.
- “Em breve” e disponibilidade em cada catálogo podem exigir consultas específicas adicionais.
- Favoritos e preferências ficam apenas no navegador atual; não sincronizam entre dispositivos.
- A lista “Quero assistir” e os favoritos são locais, sem conta ou backend.
- A pesquisa implementada pesquisa título de filme. Busca avançada por ator/diretor pode ser adicionada usando `/search/person` e consultas de créditos.
- O filtro de streaming utiliza provedores disponíveis na API regional; os resultados dependem dos parâmetros de descoberta suportados pela API.
- Este projeto não fornece nem reproduz filmes.

## Atribuição e marca

Este produto utiliza a API do TMDB, mas não é endossado ou certificado pelo TMDB. Consulte as regras atuais de atribuição e uso comercial antes de publicar:
- https://developer.themoviedb.org/docs/getting-started
- https://developer.themoviedb.org/docs/faq
- https://www.themoviedb.org/terms-of-use

Os dados de disponibilidade de streaming são fornecidos por TMDB/JustWatch. Inclua os créditos e logotipos exigidos pela política vigente, e não use marcas de serviços de streaming de forma que sugira parceria ou endosso.

## Estrutura

```text
CineBusca/
├── index.html
├── package.json
├── .env.example
├── .gitignore
├── README.md
└── src/
    ├── main.jsx
    ├── App.jsx
    └── App.css
```
