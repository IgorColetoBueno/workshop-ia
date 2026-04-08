Este documento é um guia completo para o time de TI da **Alpha Software** dominar o uso de Inteligência Artificial em tarefas de engenharia de software, abrangendo programação, design, gestão de projetos e resolução de problemas.

---

## 🧠 Como a IA funciona por baixo dos panos

A IA generativa (como modelos da Anthropic, OpenAI, etc.) funciona com base em Modelos de Linguagem Grande (LLMs). Estes modelos são vastas redes neurais treinadas para compreender padrões e prever as próximas palavras de uma sequência.

No contexto de agentes de código (como Cursor, Claude Code ou Codex):

- **Análise Semântica:** A IA não atua apenas pesquisando texto, ela compreende a lógica e a intenção arquitetural do código.
- **RAG (Retrieval-Augmented Generation):** O agente busca informações ativamente nos seus arquivos, no histórico do terminal e na árvore de dependências para montar um contexto super-rico antes de enviar o prompt final ao modelo.
- **Uso de Ferramentas:** A IA pode invocar comandos locais, ler/escrever arquivos e buscar na web de forma autônoma para resolver problemas passo a passo.

---

## 🎯 Como fornecer o melhor contexto

O sucesso com a IA depende inteiramente de como você se comunica com ela. Siga estas diretrizes:

1. **Seja específico e claro:** Em vez de dizer "arrume o bug", use "O botão de login não responde na página X quando o usuário está deslogado. Verifique o componente Button.tsx".
2. **Mostre o que já tentou:** Conte as soluções que falharam. Isso evita que a IA ande em círculos repetindo as mesmas sugestões.
3. **Anexe as referências certas:** Se um erro envolve o banco de dados e um script, anexe ambos no chat utilizando as menções (ex: `@arquivo`).
4. **Divida problemas grandes:** Peça para a IA resolver pequenos blocos de cada vez em vez de refatorar o sistema inteiro em um único prompt.
5. **Use o modo correto:** Se precisar planejar uma funcionalidade complexa, use o modo de "Planejamento" (Plan mode). Se a decisão já foi tomada e é hora de codificar, alterne para o modo "Agente".

---

## 🔌 O que é MCP e como ele melhora o trabalho?

**MCP (Model Context Protocol)** é um protocolo de código aberto que padroniza como as ferramentas de Inteligência Artificial se conectam a fontes de dados externas. Ele permite que os agentes de IA leiam, busquem e interajam com serviços de terceiros de maneira segura e direta, poupando você de ficar copiando e colando documentações o tempo todo.

Pesquisei as ferramentas utilizadas na empresa e como você pode integrá-las aos seus agentes de IA:

### 📣 Comunicação e Gestão

- **Slack:** É recomendado instalar o [**Slack MCP Server**](https://slack.com/intl/pt-br/help/articles/48855576908307-Guia-do-servidor-MCP-do-Slack). Com ele, a IA pode buscar o contexto de mensagens e resumir discussões relevantes das threads diretamente no seu editor.
- **Jira:** Recomendamos o [Atlassian MCP Server](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/). Ele possibilita que a IA leia requisitos das tarefas e atualize o status dos seus tickets.
- **Confluence:** Sugerimos utilizar o [**Atlassian MCP Server**](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/) para permitir que o agente puxe documentações e diretrizes de produto instantaneamente.
- **Mindmeister:** Você pode utilizar um [MCP](https://viasocket.com/mcp/mindmeister) de mapas mentais (como o projeto da comunidade `mindm-mcp` ou `viasocket/mindmeister`) para consultar e manipular lógicas esquematizadas nas suas árvores mentais. Eu não cheguei a testar este MCP.

### 🎨 Design e Organização

- **Figma:** Utilize o [**Figma MCP Server**](https://www.figma.com/pt-br/mcp-catalog/) para integrar os designs do seu time de UX/UI com a codificação frontend que a IA está gerando.
- **Obsidian:** Sendo uma ferramenta de base de conhecimento (semelhante ao Notion, mas operando com arquivos Markdown locais e links bidirecionais), você pode e deve integrá-la. Recomendamos instalar o servidor **`obsidian-mcp-server`** (ou `mcp-obsidian`) em conjunto com o plugin comunitário *Local REST API* no seu vault. Mais detalhes [aqui](https://github.com/cyanheads/obsidian-mcp-server).

### 💻 IDEs e Engenharia

- **Visual Studio / Visual Studio Code:** Recomendo instalar extensões de IA como **Claude Code**, **Codex**, ou as extensões nativas do GitHub Copilot.
- **GitHub:** Recomendamos instalar o **[GitHub CLI](https://cli.github.com/)** nativo do sistema. O MCP do Github até existe, mas o CLI é muito melhor. As IAs são ótimas em usar ferramentas de linha de comando.

### 🗄️ Bancos de Dados e APIs

- **DBeaver e MsManager:** O MsManager é uma ferramenta legada de SQL Server. A recomendação moderna para trabalhar com IA é usar o DBeaver. Você pode utilizar o pacote **`@iflow-mcp/dbeaver-mcp-server`** ou a versão **DBeaver PRO 26.0**, que já possui capacidades de atuar como servidor MCP nativamente. Para conexões estritas em SQL Server, servidores como `mssql_mcp_server` ou `mssql-mcp` são excelentes. Mais detalhes [aqui](https://github.com/srthkdev/dbeaver-mcp-server).
- **Postman:** Com o recém-lançado [**Postman API MCP Server**](https://www.postman.com/product/mcp-server/) oficial, a IA pode consultar todas as suas coleções de APIs, workspaces e *mock servers* para escrever código de integração quase perfeito.

### ☁️ Infraestrutura Cloud e Hospedagem

- [**MonsterASP.NET](http://monsterasp.net/), [SmarterASP.NET](http://smarterasp.net/) e CloudClusters:** Atualmente, **não** existem servidores MCP públicos ou nativos disponíveis para estas ferramentas específicas de infraestrutura.
- **Excalidraw:** Nenhuma ação com MCP é estritamente necessária no momento.

---

## 📜 O que são Regras, Skills e Comandos

Ao usar agentes focados em código (como o Cursor, Claude Code, Codex etc), você pode automatizar comportamentos com:

- **Regras (Rules):** São arquivos permanentes (como o `.cursorrules` na raiz do projeto) Onde você documenta decisões arquiteturais fixas. Ex: "Sempre use Tailwind" ou "Nunca utilize var no JS". O agente segue essas regras em todas as interações.
- **Skills (Habilidades):** São roteiros ou capacidades extras fornecidas por plugins. As skills ensinam à IA fluxos de trabalho completos, permitindo que ela invoque outras ferramentas por trás dos panos para atingir o objetivo (ex: como ler e processar uma página inteira de requisitos).
- **Comandos (Commands):** Invocações manuais e atalhos rápidos de teclado ou chat (geralmente ativados ao digitar `/`) que dão *start* instantâneo a uma Skill ou a uma tarefa repetitiva.

---

## 🛠️ Como criar suas próprias skills no seu projeto

Se a equipe da Alpha Software tiver fluxos de revisão próprios ou regras de segurança específicas, vocês podem criar skills customizadas:

1. **Crie a documentação da Skill:** Crie um arquivo Markdown no projeto (ex: `.(cursor|claude)/skills/RevisaoDeCodigo.md`) detalhando como o agente de IA deve se portar para revisar e consertar algo específico do seu domínio de TI.
2. **Defina as integrações:** Se a skill envolver checar o banco de dados antes do deploy, garanta que os servidores MCP necessários (como os de SQL/DBeaver) estejam rodando e disponíveis.
3. **Configure o escopo:** Especifique, no próprio arquivo da skill, em quais situações ela deve atuar.
4. **Acione a Skill:** Para executar seu fluxo, mencione o arquivo da skill diretamente no prompt do chat (ex: `@RevisaoDeCodigo.md`) para forçar o agente a seguir o plano definido por vocês.

Algumas skills populares na web podem simplesmente instaladas:
* .NET skills: https://github.com/wshaddix/dotnet-skills
* React: https://vercel.com/docs/agent-resources/skills
