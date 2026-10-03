# Sénior

> **Do júnior ao sénior, um artigo de cada vez.**

Site editorial e guia de programação mantido por **Inyluar**, focado em fundamentos que aguentam o tempo, decisões de carreira e arquitetura de software — sem enrolação.

---

## 📌 Índice

- [Sobre o projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Stack técnica](#-stack-técnica)
- [Estrutura do projeto](#-estrutura-do-projeto)
- [Como executar localmente](#-como-executar-localmente)
- [Deploy](#-deploy)
- [Publicidade (ADS Terra)](#-publicidade-ads-terra)
- [Personalização](#-personalização)
- [Acessibilidade e performance](#-acessibilidade-e-performance)
- [Roadmap](#-roadmap)
- [Licença](#-licença)
- [Contacto](#-contacto)

---

## 🧭 Sobre o projeto

**Sénior** é um site estático de artigo único (`single-page`) que reúne:

- Uma **página editorial** com artigos filtrados por categoria (Lua, Luar, Syze, Nyx, Orbe).
- Um **Guia de Programação** interativo com comandos e exemplos completos de **HTML, Python, Lua e JavaScript**, mais um comparativo entre as quatro linguagens.
- Uma secção **Sobre** e um **Menu lateral** com personalização de aparência em tempo real.

O objetivo editorial é ajudar quem programa a deixar de aplicar soluções de cor e passar a entender o *porquê* — o percurso de júnior a sénior, artigo a artigo.

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| 🗂️ **Filtro por categoria** | Pills clicáveis que filtram artigos na Home e na página de Artigos |
| 📚 **Guia interativo** | 5 abas (HTML, Python, Lua, JavaScript, Comparativo) com tabelas de comandos e exemplos reais |
| 🎨 **5 cores de destaque** | Dourado, Azul, Verde, Roxo, Rosa — aplicadas em tempo real |
| 🌗 **2 temas** | Minimalista (claro) e Liquid Glass (escuro com blur) |
| 🔠 **3 tamanhos de fonte** | Pequena, Média, Grande |
| 📐 **3 densidades** | Compacto, Confortável, Espaçoso |
| 💾 **Persistência** | Preferências guardadas em `localStorage` |
| 🧭 **Router SPA** | Navegação entre ecrãs sem recarregar, com `hash` na URL |
| 📱 **Responsivo** | Layout adaptado a telemóvel, tablet e desktop |
| 🔒 **Proteção básica** | Dissuasor de `right-click`, `F12`, `Ctrl+U`, `Ctrl+S` |
| 💰 **Monetização** | Integração completa com **ADS Terra** (banner, native in-feed, popunders, link direto) |

---

## 🛠️ Stack técnica

- **HTML5** semântico
- **CSS3** com variáveis (`custom properties`), `grid`, `flexbox` e `backdrop-filter`
- **JavaScript** puro (Vanilla JS, sem frameworks)
- **SVG inline** para logótipo e favicon (zero pedidos externos)
- **Google Fonts** — Lora, Inter, JetBrains Mono
- **localStorage** para preferências do utilizador

Não há build step, bundler, npm, nem dependências a instalar. **É um único ficheiro `.html`.**

---

## 📁 Estrutura do projeto

```
senior/
├── index.html          # Ficheiro único — todo o site
├── README.md           # Este ficheiro
└── LICENSE             # Licença de uso (ver secção Licença)
```

> O site foi deliberadamente construído como **um único ficheiro HTML** para simplificar o deploy e reduzir pedidos HTTP.

---

## 🚀 Como executar localmente

Não é preciso servidor. Basta:

```bash
# 1. Clonar o repositório
git clone https://github.com/<o-teu-utilizador>/senior.git
cd senior

# 2. Abrir no navegador
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

Ou, para servir por HTTP (recomendado para testar os anúncios corretamente):

```bash
# Com Python 3
python -m http.server 8080

# Com Node.js
npx serve .

# Com PHP
php -S localhost:8080
```

Depois abre `http://localhost:8080` no navegador.

---

## 🌐 Deploy

Por ser um ficheiro estático, o deploy é imediato em qualquer serviço:

### GitHub Pages
1. Faz push do `index.html` para a branch `main`.
2. **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. O site fica disponível em `https://<utilizador>.github.io/senior/`.

### Netlify / Vercel / Cloudflare Pages
1. Arrasta a pasta do projeto para o painel do serviço.
2. Deploy automático — não precisa de configuração.

### Servidor próprio (cPanel, VPS)
1. Faz upload do `index.html` para a pasta pública (`public_html`, `www`, etc.).
2. Pronto.

---

## 💰 Publicidade (ADS Terra)

O site tem **quatro camadas de monetização** integradas pela plataforma *ADS Terra / ProfitablerateCPM*:

| Camada | Formato | Localização no HTML | Objetivo |
|---|---|---|---|
| 1 | **Popunder** (×2) | `<head>` | Receita passiva em qualquer clique |
| 2 | **Banner 468×60** | Imediatamente abaixo do `<header>` | Impressão *above-the-fold* |
| 3 | **Native in-feed** | Injetado na grelha de artigos (4ª linha) | CTR elevado — parece editorial |
| 4 | **Link direto** | Rodapé, coluna *Legal* | Capta cliques informativos |

### Notas importantes

- ⚠️ **Não alterar o `id="container-9d5aa6d87eb95764765015ebe59b5626"`** — o script `invoke.js` procura-o por esse ID exato.
- ⚠️ **A ordem `atOptions` → `invoke.js`** deve ser mantida (o `atOptions` define a configuração lida pelo `invoke.js`).
- ⚠️ **Bloqueadores de anúncios** (uBlock, AdBlock, Brave Shield) impedem o carregamento dos scripts — comportamento esperado.
- ℹ️ Os scripts só geram receita **em produção, com um domínio registado** na plataforma. Em `localhost` podem não render.

### Como alterar os IDs de anúncio

Se precisares de trocar os IDs (por exemplo, para uma nova conta), procura no `index.html` por:

```
atOptions = { 'key' : '...' }      → banner 468×60
container-9d5aa6d8...              → native in-feed
pl31646614 / pl31646615 / pl31646617 → popunders
profitableratecpmnetwork.com/mw6fpipwjh?key=... → link direto
```

Substitui apenas as chaves e os IDs, mantendo a estrutura.

---

## 🎨 Personalização

### Alterar as cores de destaque

No `<style>`, procura `body.accent-*`:

```css
body.accent-gold   { --accent:#A9782E; }
body.accent-blue   { --accent:#3155C4; }
body.accent-green  { --accent:#1F8A5C; }
body.accent-purple { --accent:#6A45D6; }
body.accent-pink   { --accent:#C23A6C; }
```

### Adicionar uma nova categoria

Em `CATEGORIAS`, dentro do `<script>`:

```js
var CATEGORIAS = [
  { id:'todos', nome:'Todos', sub:'' },
  { id:'nova',  nome:'Nova',  sub:'subtítulo' },  // ← adiciona aqui
  // ...
];
```

E adiciona artigos correspondentes em `ARTIGOS` com `cat:'nova'`.

### Adicionar um artigo

```js
{ cat:'lua', tag:'Lua · Fundamentos',
  titulo:'Título do artigo',
  desc:'Resumo curto que aparece no cartão.',
  data:'01 OUT', min:'5 min' }
```

---

## ♿ Acessibilidade e performance

- Contraste AA na maioria dos elementos de texto.
- Navegação por teclado no menu lateral (`Escape` fecha, foco em botões).
- `aria-label` em botões icónicos.
- SVGs com `aria-hidden` quando decorativos.
- **Zero dependências externas de JS** — só as fontes do Google.
- Imagens inline (SVG) evitam pedidos de rede.
- `font-display: swap` implícito via Google Fonts.
- Sem impacto relevante nos Core Web Vitals (formato estático + SVG).

---

## 🗺️ Roadmap

- [ ] Sistema de artigos em Markdown com renderização dinâmica
- [ ] Modo leitura (remove anúncios e distrações, exceto o banner de topo)
- [ ] Lazy-load do native in-feed (só carrega quando entra no viewport)
- [ ] Página de artigo individual com URL própria
- [ ] Pesquisa full-text nos artigos e no guia
- [ ] Suporte a PWA (instalável, com cache offline)
- [ ] Suporte i18n (pt-PT / en)

---

## 📄 Licença

**© 2026 Sénior · Inyluar. Todos os direitos reservados.**

Este projeto é de **código fechado**. Uso, cópia, redistribuição ou modificação **não autorizados** são proibidos, salvo autorização expressa e por escrito do autor.

Para pedidos de licenciamento, contacto ou colaboração editorial, usa o email indicado abaixo.

---

## 📬 Contacto

- **Autor:** Inyluar
- **Email:** [inygujamo87@gmail.com](mailto:inygujamo87@gmail.com)
- **Repositório:** [github.com/&lt;utilizador&gt;/senior](https://github.com/)

---

<p align="center">
  <sub><b>Sénior</b> — escrito por Inyluar. © 2026. Todos os direitos reservados.</sub>
</p>
