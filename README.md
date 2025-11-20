# 🚀 Nikel: Sistema de Controle Financeiro Pessoal

O Nikel é uma aplicação web simples e responsiva para gerenciamento financeiro pessoal, focada no registro e visualização de transações (entradas e saídas).

## 💡 Tecnologias Utilizadas

| Tecnologia | Função Principal |
| :--- | :--- |
| **HTML5** | Estrutura semântica das páginas. |
| **CSS3** | Estilização, *layout* e identidade visual. |
| **Bootstrap 5.1.3** | Framework de *front-end* para *layout* responsivo e componentes (Navbar, Modal, Formulários). |
| **Bootstrap Icons** | Biblioteca de ícones (moedas, pessoa, casa, etc.). |
| **JavaScript** | Lógica de autenticação, manipulação de dados, e atualização dinâmica da interface (DOM). |
| **`localStorage` / `sessionStorage`** | Persistência de dados e gerenciamento de sessão no navegador. |

---

## 📁 Estrutura do Projeto e Arquivos

O projeto é dividido em três telas principais (HTML) e seus respectivos *scripts* de suporte (JS), além de um arquivo CSS compartilhado:

| Arquivo HTML | Script JS Associado | Função da Tela |
| :--- | :--- | :--- |
| **`index.html`** | `index.js` | Login e Cadastro de Usuários. |
| **`home.html`** | `home.js` | Dashboard (Saldo total e últimos 5 lançamentos). |
| **`transactions.html`** | `transactions.js` | Listagem Completa de Lançamentos em formato de tabela. |
| **`styles.css`** | N/A | Estilização Global e Layout. |

---

## 💻 Interação entre HTML, JavaScript e CSS

### 1. **`index.html` + `index.js` (Autenticação)**

O `index.js` é o motor da autenticação, interagindo com o `index.html` da seguinte forma:

* **Criação de Conta:** O formulário dentro da modal (`id="create-form"`) envia os dados. O `index.js` armazena o novo usuário (e-mail, senha e `transactions: []`) no **`localStorage`**.
* **Login:** O formulário de login (`id="login-form"`) é processado. Se as credenciais estiverem corretas, o e-mail é salvo no **`sessionStorage`** (e no `localStorage` se a opção "Permanecer logado" for marcada).
* **Redirecionamento:** Após o login ou se uma sessão for detectada (`checkLogged()`), o usuário é redirecionado para **`home.html`**.

### 2. **`home.html` + `home.js` (Dashboard)**

O `home.js` gerencia a visualização resumida e a adição de novos lançamentos na tela principal:

* **Carregamento de Dados:** Ao carregar, o `home.js` usa o e-mail da sessão para buscar e carregar o objeto de dados do usuário (incluindo todas as transações) do **`localStorage`**.
* **Cálculos e Exibição:**
    * `getTotal()`: Calcula o balanço líquido (Entradas - Saídas) e atualiza o elemento `<span id="total">` no HTML.
    * `getCashIn()` / `getCashOut()`: Filtram as transações e geram HTML dinamicamente, injetando os **últimos 5 lançamentos** nas listas `id="cash-in-list"` e `id="cash-out-list"`.
* **Adicionar Transação:** O formulário da modal de lançamento (`id="transaction-form"`) coleta os dados e o `home.js` salva a nova transação no array e atualiza o **`localStorage`** (`saveData()`).

### 3. **`transactions.html` + `transactions.js` (Detalhes)**

O `transactions.js` é especializado em exibir o histórico completo:

* **Listagem Completa:** A função `getTransactions()` itera sobre *todas* as transações do usuário, cria linhas de tabela (`<tr>`) com Data, Valor, Tipo e Descrição, e injeta-as no `<tbody>` da tabela (`id="transactions-list"`).
* **Modal de Lançamento:** A tela reutiliza a modal e o formulário de transação. Após a submissão, o `transactions.js` atualiza o `localStorage` e recarrega a tabela completa.

---

## 🎨 Estilização (`styles.css`)

O CSS atua na formatação visual e funcional do projeto:

* **Identidade Visual:** Define as cores primárias (**Roxo Escuro: `#4e0070`**) e secundárias (**Azul Claro: `#4c79d3`**), usadas em textos, links e botões.
* **Layout de Fundo:** Utiliza `linear-gradient` para criar uma separação visual diagonal distinta:
    * Fundo de **Login (`#login`)** em Azul Claro/Branco.
    * Fundo da **Aplicação (`#app`)** em Branco/Azul Claro.
* **Componentes:**
    * **Botões de Ação:** `.button-login` e `.button-default` utilizam a cor primária e têm efeitos *hover* que mudam para a cor secundária.
    * **Botão Flutuante:** O `.button-float` utiliza `position: fixed` e `border-radius: 100%` para fixar o botão **`+`** (Adicionar Lançamento) no canto inferior direito da tela.
    * **Área de Informações:** O `.info` (nas telas `home` e `transactions`) usa `background-color: #ffffff` e `border-radius` para criar um painel visualmente destacado com cantos arredondados na parte superior.


## 7. 👩‍💻 Autora

**Stefany Batista**
* Estudante de Sistemas de Informação
* Foco em Desenvolvimento e Dados.

[LinkedIn](www.linkedin.com/in/stefanybrauns) | [GitHub do projeto](https://github.com/Fanaste/Projeto_Nikel))
