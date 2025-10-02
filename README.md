# AGROCITRO-FINAL 🌱 

## Leonardo Augusto de Souza Silva, Kaio Antony Alves de Oliveira, Isaac Iuri Alves de Oliveira, Maria Clara Silva Galindo 

O **AgroCitro** é um sistema web voltado para o **gerenciamento de atividades agrícolas**, integrando páginas dinâmicas (**HTML, CSS e JavaScript**), um **servidor Node.js** e um **banco de dados SQL** para armazenamento de informações.  

Este projeto foi desenvolvido com foco acadêmico, buscando unir **tecnologia e agricultura** para criar uma solução digital simples, prática e educativa para acompanhar as principais etapas do cultivo.  

---

## 🎯 Objetivos
- Facilitar a organização das etapas do processo agrícola.  
- Disponibilizar uma interface simples para visualização de **plantio, irrigação, colheita e manejo de mudas**.  
- Integrar um banco de dados relacional para persistência de informações.  
- Servir como prática de **desenvolvimento fullstack** (frontend + backend + banco de dados).  

---

## ⚙️ Funcionalidades
- 🌱 **Plantio** – registro e acompanhamento das etapas de plantio.  
- 💧 **Irrigação** – organização e controle de técnicas de irrigação.  
- 🌾 **Colheita** – informações e dados sobre o processo de colheita.  
- 🌳 **Mudas** – gerenciamento das mudas cultivadas.  
- 💾 Integração com **MySQL** através de scripts SQL (`agrocitro.sql`).  

---

## 🛠️ Tecnologias
- **Frontend**: HTML5, CSS3, JavaScript  
- **Backend**: Node.js + Express  
- **Banco de Dados**: MySQL2  
- **Gerenciador de pacotes**: npm  

---

# Codigos💻

## Pré-requisitos

Para rodar esta aplicação, você deve ter instalado:

- [Node.js](https://nodejs.org/) (e, por consequência, o npm - Node Package Manager).
- Um servidor de banco de dados [MySQL](https://www.mysql.com/) ou [MariaDB](https://mariadb.org/).

Aqui está o conteúdo em formato Markdown (`README.md`):

````markdown
# Sistema de Gerenciamento de Plantio, Irrigação e Colheita

Esta aplicação backend é desenvolvida com Node.js e Express, projetada para gerenciar as operações de plantio, irrigação e colheita de um sistema agrícola. O servidor usa os drivers `mysql` e `mysql2` para se conectar a um banco de dados relacional e executar operações de CRUD (Create, Read, Update, Delete) através das rotas da API.

## ⚙️ Pré-requisitos

Antes de rodar a aplicação, certifique-se de ter os seguintes pré-requisitos instalados:

- [Node.js](https://nodejs.org/) (inclui o npm - Node Package Manager).
- Um servidor de banco de dados [MySQL](https://www.mysql.com/) ou [MariaDB](https://mariadb.org/).

## 🛠️ Configuração e Instalação

### Passo 1: Obter os Arquivos

Certifique-se de que os arquivos `package.json`, `server.js` e a pasta `repositorio` (contendo o arquivo `bancoDados.js`) estão na mesma pasta.

### Passo 2: Instalar Dependências

No terminal, navegue até o diretório do projeto e execute o comando para instalar as dependências:

```bash
npm install
````

As dependências instaladas serão:

* `express`
* `mysql`
* `mysql2`

### Passo 3: Configurar o Banco de Dados

**Atenção:** O código depende de um arquivo de módulo de banco de dados (`./repositorio/bancoDados.js`), que não foi incluído, mas é essencial para a conexão.

#### Criação do Banco

Crie o banco de dados no seu servidor MySQL:

```sql
CREATE DATABASE farm_manager;
```

#### Configuração da Conexão

Configure as credenciais de conexão (host, usuário, senha, nome do banco) dentro do arquivo `./repositorio/bancoDados.js`.

#### Implementação das Funções

O arquivo `bancoDados.js` deve conter e exportar as funções utilizadas pelo `server.js`, como:

* `obterPlantios`
* `incluirPlantios`
* `obterTotalMudas`
* `obterIrrigacao`
* `incluirIrrigacao`
* `obterColheita`
* `incluirColheita`

#### Estrutura das Tabelas

Garanta que as tabelas necessárias (por exemplo: `Plantios`, `Irrigacao`, `Colheita`) estejam criadas no banco de dados para que as queries SQL executadas pelas funções não falhem.

### Passo 4: Inicializar o Servidor

Com as dependências instaladas e o banco de dados configurado, inicie o servidor com o script definido no `package.json`:

```bash
npm start
```

Ou, alternativamente, execute diretamente o arquivo:

```bash
node server.js
```

Se a inicialização for bem-sucedida, você verá a seguinte mensagem no terminal:

```
Servidor OnLine!
O servidor estará escutando na porta 3000.
```

## 🚀 Rotas da API (Endpoints)

A aplicação expõe os seguintes endpoints HTTP, rodando em `localhost:3000`:

| Método | Endpoint            | Descrição                                                | Dados Necessários (Body JSON)                                 |
| ------ | ------------------- | -------------------------------------------------------- | ------------------------------------------------------------- |
| GET    | /plantios           | Retorna a lista de todos os registros de plantio.        | N/A                                                           |
| POST   | /registrarPlantio   | Registra um novo plantio no banco de dados.              | `{Variedade, Data_Plantio, Quantidade_Plantada, Localizacao}` |
| GET    | /mudas              | Retorna o total de mudas e a data da última atualização. | N/A                                                           |
| GET    | /irrigacao          | Retorna a lista de todos os registros de irrigação.      | N/A                                                           |
| POST   | /registrarIrrigacao | Registra uma nova sessão de irrigação.                   | `{ID_Plantio, Horario_Inicial, Horario_Final}`                |
| GET    | /colheita           | Retorna a lista de todos os registros de colheita.       | N/A                                                           |
| POST   | /registrarColheita  | Registra uma nova colheita para um plantio.              | `{ID_Plantio, Data_Colheita, Quantidade_Colhida, Qualidade}`  |

## 📝 Exportar para as Planilhas

### Testando a API

Você pode testar essas rotas usando ferramentas de desenvolvimento como [Postman](https://www.postman.com/), [Insomnia](https://insomnia.rest/) ou `curl`.

#### Exemplo de Sucesso para POST (em todas as rotas de registro):

```json
{
    "msg": "Atualizado!"
}
```

#### Exemplo de Falha na Rota `/registrarIrrigacao` (se faltar algum campo):

```json
{
    "msg": "Todos os campos são obrigatórios."
}
```
