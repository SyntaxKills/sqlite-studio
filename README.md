# 🗄️ SQLite Studio

<p align="center">
  <strong>Uma IDE SQL moderna, profissional e autocontida para navegador, alimentada por WebAssembly.</strong>
</p>

<p align="center">
  <a href="https://syntaxkills.github.io/sqlite-studio" target="_blank" rel="noopener noreferrer">
    <img src="https://img.shields.io/badge/%E2%96%B6%20Abrir%20site-22C55E?style=for-the-badge&logoColor=white&labelColor=16A34A" alt="Abrir site" height="42" />
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/SQLite-WebAssembly-003B57?style=flat-square&logo=sqlite&logoColor=white" alt="SQLite WASM" />
  <img src="https://img.shields.io/badge/Arquitetura-Single--File%20(index.html)-2563EB?style=flat-square" alt="Single File Architecture" />
  <img src="https://img.shields.io/badge/UI%2FUX-Dark%20%2B%20Blue%20Theme-0D1420?style=flat-square" alt="Dark Theme" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT License" />
</p>

---

## 📌 Visão Geral

O **SQLite Studio** é um ambiente de desenvolvimento SQL completo e funcional que roda inteiramente no navegador do usuário via **WebAssembly (`sql.js`)**. 

Diferente de demonstrativos visuais ou protótipos com dados simulados, o SQLite Studio executa instruções SQL **reais** diretamente na memória da aba, sem a necessidade de servidores backend ou banco de dados externo.

Toda a aplicação é estruturada em um único arquivo (`index.html`), mantendo padrões elevados de arquitetura de software, acessibilidade e design de interface (UI/UX) inspirado em IDEs como VS Code.

---

## 🖼️ Visão da Interface (Tela Única)

Toda a interação ocorre em uma **única tela**, dividida estrategicamente para máxima produtividade:

```
+---------------------------------------------------------------------------------+
| 🗄️ SQLite Studio               [ SQLite WASM ] [ In-Memory ]   🟢 SQLite pronto |
+---------------------------------------------------------------------------------+
| EDITOR SQL                                        [ Ctrl + Enter ] [ ▶ Run ] [ Clear ] |
|---------------------------------------------------------------------------------|
| 1 | CREATE TABLE usuarios (id INTEGER PRIMARY KEY, nome TEXT, email TEXT);      |
| 2 | INSERT INTO usuarios VALUES (1, 'Alice', 'alice@dev.com');                  |
| 3 | SELECT * FROM usuarios;                                                     |
|                                                                                 |
+---------------------------------------------------------------------------------+
| CONSOLE DE EXECUÇÃO                                             3 execuções     |
|---------------------------------------------------------------------------------|
| [ SUCESSO ] [ CREATE ]  1.20 ms  21:45:00                                      |
| Operação CREATE concluída com sucesso.                                          |
|                                                                                 |
| [ SUCESSO ] [ SELECT ]  0.85 ms  21:45:02                                      |
| +----+---------+-----------------+                                              |
| | id | nome    | email           |                                              |
| +----+---------+-----------------+                                              |
| | 1  | Alice   | alice@dev.com   |                                              |
| +----+---------+-----------------+                                              |
| 1 linha(s) retornada(s) (3 coluna(s)).                                          |
+---------------------------------------------------------------------------------+
| 🌐 SQLite Studio                                       [ 💬 Relatar problema ]  |
+---------------------------------------------------------------------------------+
```

---

## 🚀 Como Acessar e Usar (Passo a Passo)

### 1. Acessando a Aplicação
Você pode utilizar o **SQLite Studio** instantaneamente online sem instalar nada:

<div align="center" style="margin: 20px 0;">
  <a href="https://syntaxkills.github.io/sqlite-studio" target="_blank" rel="noopener noreferrer" style="text-decoration: none;">
    <button style="background-color: #22c55e; color: #052e16; border: 1px solid #16a34a; padding: 12px 24px; font-size: 16px; font-weight: 700; border-radius: 6px; cursor: pointer;">
      ▶ Abrir site
    </button>
  </a>
</div>

---

### 2. Aguarde a Inicialização do SQLite
Ao abrir o site, verifique a barra superior no canto direito:
* **🟢 SQLite pronto**: A engine WebAssembly foi carregada e o banco de dados em memória está ativo.
* **🟡 Inicializando SQLite...**: Aguarde o carregamento dos arquivos `.wasm` via CDN.

---

### 3. Escrevendo e Editando SQL
No painel **Editor SQL**:
* Digite suas instruções SQL (DDL, DML, DQL).
* O editor inclui **syntax highlighting** (destaque de palavras-chave, números, strings e comentários), numeração de linhas e recuo automático.
* **Atalhos de teclado úteis:**
  * `Ctrl + Enter` (ou `Cmd + Enter` no Mac): Executa o script completo.
  * `Ctrl + Z`: Desfaz alterações no texto.
  * `Ctrl + A`: Seleciona todo o script.
  * `Tab`: Indenta linhas selecionadas.

---

### 4. Executando Comandos (`▶ Run`)
Clique no botão verde **▶ Run** ou pressione `Ctrl + Enter`.
* **Execução Múltipla:** É possível enviar múltiplos comandos separados por `;`.
* **Preservação de Dados:** O banco em memória permanece ativo durante toda a sessão. Se você criar uma tabela (`CREATE TABLE`), inserir dados (`INSERT`) e depois fizer uma consulta (`SELECT`), os dados continuarão lá.

---

### 5. Analisando a Saída no Console
O painel **Console** exibe os resultados organizados por ordem cronológica:
* **Instruções `SELECT`:** Renderizam os dados em uma tabela HTML interativa com suporte a rolagem horizontal, valores `NULL` destacados e limitação visual para grandes volumes de registros.
* **Comandos de Alteração (`INSERT`, `UPDATE`, `DELETE`):** Informam o número exato de linhas afetadas e o tempo de execução em milissegundos.
* **Tratamento de Erros:** Erros de sintaxe ou tabelas inexistentes são capturados sem travar a aplicação, exibindo alertas visuais em vermelho com diagnósticos úteis.

---

### 6. Limpando a Interface (`Clear`)
Clique no botão vermelho **Clear**:
* **O que faz:** Limpa o conteúdo do editor e o histórico do console de execução.
* **O que NÃO faz:** **Não destrói** o banco de dados da sessão. Suas tabelas e registros permanecem preservados em memória.

---

### 7. Relatando Problemas (`Relatar problema`)
Se você encontrar um bug ou erro de execução:
1. Clique no botão **Relatar problema** no canto inferior direito.
2. Escreva uma descrição detalhada do problema no painel lateral.
3. Ao clicar em **Enviar**, o sistema valida a mensagem, gera os metadados da sessão (timestamp, estado da engine, versão) e direciona para o repositório oficial no GitHub (`SyntaxKills/sqlite`) de maneira segura sem expor credenciais no cliente.

---

## 🛠️ Tecnologias Utilizadas

* **HTML5 Semantic**: Estrutura acessível e responsiva.
* **CSS3 Custom Properties**: Tema escuro profissional (`#090D14` / Azul `#2563EB`).
* **JavaScript Vanilla (ES6+)**: Sem frameworks pesados ou processos de build.
* **sql.js (WebAssembly)**: Engine SQLite compilada para C/WASM rodando 100% no cliente.
* **CodeMirror 5**: Editor de código com realce de sintaxe SQL.

---

## 🔒 Segurança e Privacidade

* **Zero backend:** Nenhum dado SQL digitado ou armazenado sai do seu navegador.
* **Sem rastreamento:** Não há coleta de métricas, cookies de terceiros ou analytics.
* **Arquitetura segura:** Integrações externas (como o formulário de relato de problemas no GitHub) seguem o modelo de não exposição de tokens de autenticação no lado do cliente.

---

## 💻 Como Executar Localmente

Como a aplicação é um arquivo único estático:

1. Clone o repositório:
   ```bash
   git clone https://github.com/SyntaxKills/sqlite.git
   ```
2. Navegue até o diretório:
   ```bash
   cd sqlite
   ```
3. Abra o arquivo `index.html` diretamente em seu navegador favorito (ou utilize um servidor estático como `npx serve` ou a extensão Live Server do VS Code).

---

<p align="center">
  Desenvolvido com foco em alta performance, usabilidade e engenharia de software limpa.
</p>
