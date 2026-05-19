# 🔧 Hardware C2C — Marketplace Nichado de Peças e Periféricos

Este repositório contém o código-fonte e a documentação do protótipo de alta fidelidade desenvolvido para a disciplina de **Interação Humano-Computador II (IHC)**. O projeto consiste em uma plataforma de e-commerce transacional C2C (Customer-to-Customer) focada exclusivamente no universo de tecnologia e hardware usado.

O sistema foi rigorosamente projetado, avaliado e refinado com base nas **10 Heurísticas de Nielsen**, diretrizes de acessibilidade **WCAG (W3C)** e padrões modernos de Engenharia de Usabilidade.

---

## 🎯 Contexto e Público-Alvo
No domínio de hardware, especificações técnicas detalhadas são fatores determinantes para a conversão. O público-alvo é composto por:
* **Estudantes de TI** (como alunos dos Institutos Federais);
* **Gamers e Entusiastas de Computadores** que montam e desmontam seus setups;
* **Vendedores casuais** que buscam desapegar de peças antigas após a realização de upgrades de componentes.

---

## 🏗️ Arquitetura da Informação e Padrões de Interface
A aplicação foi estruturada como uma **Single Page Application (SPA)** em HTML5, CSS3 estruturado e Vanilla JavaScript, garantindo alta performance e persistência local de estados através de `localStorage`.

### Padrões de UX Aplicados:
1.  **Cards de Produto:** Visuais limpos contendo foto principal da categoria, título, condição de uso e preço proeminente.
2.  **Filtros Facetados (Sidebar):** Menu de filtragem lateral responsivo para refinamento instantâneo por *Categoria* e *Condição*, contendo gerenciamento nativo de *Empty States* interativos.
3.  **Breadcrumbs (Trilha de Migalhas):** Navegação estrutural explícita (`Início > Categoria > Nome do Produto`) na página de detalhes para contextualização espacial do usuário.
4.  **Wizard Step-by-Step:** Fluxo em abas para a publicação de novos anúncios, quebrando formulários longos em etapas cognitivas menores (Dados Básicos, Specs Técnicas e Revisão Transacional).
5.  **Chat C2C Integrado:** Módulo simulado de negociação entre comprador e vendedor para envio de dúvidas e fechamento da venda de forma segura.

---

## 🛡️ Engenharia de Usabilidade: Heurísticas Aplicadas e Refinamentos Críticos

Durante os ciclos de Avaliação Heurística e Maquetaria Digital, foram aplicados ajustes finos e rigorosos para eliminação completa de erros de usabilidade:

### 1. Feedback Visual e Visibilidade do Status do Sistema (Heurística #1)
* **Estado de Carregamento nos Botões:** Ações transacionais ou de autenticação (como *Fazer Login* e *🚀 Publicar*) ganharam a classe `.btn-loading`. Ao clicar, o texto original é ocultado e um *spinner* CSS nativo é renderizado, enquanto os eventos de ponteiro são desabilitados (`pointer-events: none`). Isso previne cliques duplicados e mitiga a ansiedade do usuário.
* **Skeleton Loading:** Simulação de carregamento de dados assíncronos ao trocar de seções na plataforma.

### 2. Prevenção e Tratamento de Erros (Heurística #4 e #5)
* **Modal Destrutivo Customizado:** Substituição completa do `confirm()` nativo do navegador por um componente global síncrono estruturado (`#dangerModal`). Ações críticas de exclusão (como remover um item do carrinho ou deletar um anúncio publicado) agora acionam uma camada em sobreposição (*overlay*) com efeito *blur*, forçando o foco de decisão do usuário dentro da identidade visual do sistema.
* **Mensagens de Erro Inline:** Marcação visual de campos obrigatórios com asterisco (`*`) e sinalização de erros de validação diretamente nos contornos dos inputs para evitar punições ou Toasts excessivamente genéricos.

### 3. Acessibilidade Semântica e Visual (Normas WCAG / W3C)
* **Correção de Contraste de Cores:** Ajuste rigoroso nas cores de botões e seletores. O botão principal de transação (classe `.btn-amber-c2c`) que utilizava fundo âmbar com texto branco (reprovado em testes de leitura de baixo contraste) foi atualizado para uma tipografia escura com peso bold (`color: #1c1c1e; font-weight: 800`), cumprindo a proporção de contraste exigida pela WCAG para fontes em tamanhos padrão.
* **Semântica para Leitores de Tela:** Vinculação explícita de todas as tags `<label>` aos seus respectivos campos de entrada de dados através do atributo `for` referenciando o `id` do `<input>` (ex: `for="loginEmail"` -> `id="loginEmail"`). Isso possibilita que tecnologias assistivas realizem a leitura contextualizada dos formulários e melhora a área clicável do elemento (foco automático ao clicar no rótulo).

---

## 🔧 Tecnologias Utilizadas
* **HTML5** (Estrutura semântica);
* **CSS3** (Layout baseado em flexbox/variáveis para o Design System e CSS Paged Media para responsividade);
* **Vanilla JavaScript (ES6+)** (Gerenciamento de rotas com a função `navigate`, manipulação do DOM e controle do estado global da aplicação via objeto `state`).

---

## 🧪 Como Executar e Testar o Projeto
Como o protótipo adota o padrão de arquitetura monolítica leve e limpa, nenhuma instalação de dependências ou servidores pesados é necessária:

1.  Faça o download do arquivo `hardware-c2c.html`.
2.  Abra o arquivo diretamente em qualquer navegador moderno (Google Chrome, Firefox, Microsoft Edge ou Safari).
3.  **Para testar o fluxo de erros e resiliência:** Utilize o botão **"⚠️ Testar Falha"** na página inicial para visualizar o comportamento do sistema e o comportamento do *Empty State* de queda de rede com recuperação automática sob demanda.
4.  **Para testar a persistência:** Crie uma conta, realize o login, publique um novo componente de hardware através do assistente (*Wizard*) e verifique sua inclusão automática na vitrine com base nos dados salvos dinamicamente no `localStorage`.
