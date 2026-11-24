# Barbie Dreamworld — Frontend (Trabalho 2)

Interface web pública do **Assistente de Estilo com IA**: formulário parametrizado
(Barbie + ocasião + preferências) que gera um look completo, dicas de refinamento
e uma foto realista da Barbie, com cópia do resultado e histórico de chat
limitado a 6 mensagens. É o frontend da API em
[`isaave/Projeto2-ApiBarbie`](https://github.com/isaave/Projeto2-ApiBarbie).

## URL pública

https://isaave.github.io/Front_apibarbie/

## Arquitetura

- `index.html`: aplicação single-file (HTML + CSS + JavaScript), sem build.
- API: `https://projeto2-apibarbie.onrender.com` (Spring Boot no Render, HTTPS).
- Swagger: https://projeto2-apibarbie.onrender.com/swagger-ui/index.html
- A chave `X-API-Key` é criada automaticamente em `POST /api/auth/api-keys` na
  primeira carga, salva no `localStorage` e renovada após `401`.
- Nenhuma credencial da IA (`GEMINI_API_KEY`) existe no frontend ou no repositório.

## Execução local

Não precisa instalar nada:

```bash
cd Front_apibarbie
python3 -m http.server 8080
```

Abra http://localhost:8080/. A aplicação continuará usando a API pública;
para apontar para outra API, defina a URL antes do script (ver abaixo).

## Variáveis de ambiente

O projeto é estático, então não há variáveis de ambiente de servidor. O modelo
da única config pública está em [`.env.example`](.env.example):

| Variável | Obrigatória | Padrão | Uso |
|---|---|---|---|
| `API_BASE_URL` | Não | `https://projeto2-apibarbie.onrender.com` | URL da API consumida pelo frontend. Em Pages, o valor padrão já está em `index.html`; para sobrescrever, defina `window.APIBARBIE_API_BASE` antes do carregamento do script. |

## Deploy

Publicado via GitHub Pages a partir da branch `main` (arquivo `.nojekyll`
incluído). Commits na branch principal atualizam o site automaticamente.
