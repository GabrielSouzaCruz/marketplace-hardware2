# 🖥️ Hardware C2C — Marketplace Nichado de Peças e Periféricos

Este repositório contém o código-fonte do protótipo de alta fidelidade de uma plataforma de e-commerce C2C (Customer-to-Customer) focada exclusivamente no universo de tecnologia e hardware. 

O projeto foi desenvolvido como trabalho prático da disciplina de **Interação Humano-Computador II (IHC)**, unindo rigorosas heurísticas de usabilidade com uma **arquitetura modular de Engenharia de Software** no front-end.

---

## 🎯 O Produto
Um marketplace desenhado para mitigar a desconfiança e o atrito na compra e venda de componentes de hardware usados. O foco foi criar uma experiência fluida para estudantes de TI, *gamers* e entusiastas que realizam *upgrades* constantes aos seus computadores.

---

## 🏗️ Arquitetura de Software (Modular)
Para garantir manutenibilidade e escalabilidade, o projeto abandonou a abordagem monolítica e adotou o padrão de **Separation of Concerns (Separação de Responsabilidades)** utilizando **Módulos ES6 (Vanilla JavaScript)**:

* **`/css/`**: Estilos divididos por domínio (`variables.css` para o Design System, `layout.css`, `components.css` e `base.css`).
* **`/js/core/`**: O coração da aplicação (Gestão de Estado, Roteamento via History API e Dados Iniciais).
* **`/js/pages/`**: Controladores de visualização isolados por ecrã (Home, Carrinho, Produto, Wizard, Login).
* **`/js/utils/`**: Funções auxiliares globais (Validações, formatação de moeda, manipulação de Modais e Toasts).

---

## 🛡️ Engenharia de Usabilidade e Acessibilidade (IHC)
O sistema foi auditado e refinado para cumprir rigorosamente as **10 Heurísticas de Nielsen** e as normativas de acessibilidade da **WCAG (W3C)**:

1. **Prevenção de Erros e Validação Inline:** Em vez de alertas genéricos e punitivos, os formulários utilizam validação em tempo real e indicam o erro visualmente no campo específico.
2. **Visibilidade do Estado (Feedback):** Ações transacionais assíncronas (como "Finalizar Compra" ou "Fazer Login") implementam *spinners* de carregamento e desabilitam botões para evitar duplicação de pedidos.
3. **Controlo e Liberdade (Wayfinding):** Integração de *Breadcrumbs* (`Início > Categoria > Produto`) e suporte nativo ao botão "Voltar" do browser através da manipulação do `History API`.
4. **Fricção Positiva (Modais Destrutivos):** Remoção de itens ou eliminação de anúncios exigem confirmação através de um modal customizado com *focus trap*, prevenindo cliques acidentais (substituindo o antigo `confirm()` do navegador).
5. **Acessibilidade Semântica (A/AA/AAA):** * Estrutura construída com tags semânticas do HTML5 (`<main>`, `<nav>`, `<form>`, `<fieldset>`).
   * Navegação por teclado ativada (`Enter` para submeter formulários, `Escape` para fechar modais).
   * Alto contraste de cores testado e rótulos (`labels`) devidamente associados aos *inputs* para leitores de ecrã (Screen Readers).

---

## 🚀 Como Executar o Projeto Localmente

Devido à utilização de **Módulos ES6** (`<script type="module">`), os browsers modernos bloqueiam a execução direta do ficheiro através do protocolo `file://` por questões de segurança (CORS). 

Para rodar o projeto, **é necessário um servidor HTTP local**:

### Opção 1: Via VS Code (Recomendado)
1. Instala a extensão **[Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)** no Visual Studio Code.
2. Abre a pasta raiz do projeto (`marketplace-hardware2`) no VS Code.
3. Clica com o botão direito no ficheiro `index.html` e escolhe **"Open with Live Server"**.
4. O projeto abrirá automaticamente no browser (geralmente em `http://127.0.0.1:5500`).

### Opção 2: Via Python (Terminal)
Se tiveres o Python instalado, abre o terminal na pasta raiz do projeto e executa:
```bash
# Para Python 3
python -m http.server 8000

```

Depois, acede a `http://localhost:8000` no teu navegador.

---

## 🛠️ Tecnologias

* **HTML5** (Semântica e Acessibilidade)
* **CSS3** (Variáveis, Flexbox, Animações Suaves)
* **JavaScript ES6+** (Módulos, Arrow Functions, LocalStorage, History API)
