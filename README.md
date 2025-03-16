# 📌 Testes de API com Postman e Relatórios Newman

Este repositório contém uma **Collection de testes do Postman** e um setup para rodar testes automatizados via **Newman**, gerando relatórios detalhados em HTML.

## 🚀 Tecnologias utilizadas
- **Postman** → Criação e execução de testes de API  
- **Newman (CLI do Postman)** → Execução automatizada dos testes  
- **Newman Reporter htmlextra** → Geração de relatórios interativos  

## 📂 Estrutura do projeto
```
📦 postman_newman_serverest  
 ┣ 📜 ServeRest_API.postman_collection.json          # Collection de testes do Postman  
 ┣ 📜 Env_ServeRest.postman_environment.json         # Variáveis de ambiente (se necessário)  
 ┣ 📜 README.md                                      # Documentação do projeto  
 ┗ 📂 newman/                                        # Relatórios gerados pelo Newman  
```

## 🚀 Testes Implementados

### **1️⃣ Listar usuários cadastrados (`GET /usuarios`)**
- ✅ **Status Code 200** – Garante que a resposta foi bem-sucedida.
- ✅ **Resposta é um JSON válido** – Verifica que o formato do corpo da resposta é JSON.

---

### **2️⃣ Cadastrar um usuário (`POST /usuarios`)**
- ✅ **Status Code 201** – Confirma que o usuário foi criado com sucesso.
- ✅ **Mensagem de sucesso** – Verifica que a resposta contém `"Cadastro realizado com sucesso"`.
- ✅ **Retorno de ID** – Confirma que a resposta inclui um `_id` válido.

📌 **Pré-requisitos:**
- 🔹 Geração automática de nome e sobrenome.
- 🔹 Geração de email dinâmico.
- 🔹 Definição de senha e status de administrador.

---

### **3️⃣ Buscar um usuário por ID (`GET /usuarios/{{UserID}}`)**
- ✅ **Status Code 200** – Confirma que o usuário foi encontrado.
- ✅ **Resposta é um JSON válido** – Verifica a estrutura da resposta.
- ✅ **Validação do ID** – Garante que o ID retornado na resposta corresponde ao ID armazenado.

---

### **4️⃣ Editar nome do usuário (`PUT /usuarios/{{UserID}}`)**
- ✅ **Status Code 200** – Confirma que a atualização foi bem-sucedida.
- ✅ **Resposta é um JSON válido** – Verifica a estrutura do JSON.
- ✅ **Mensagem de sucesso** – Valida se a mensagem de retorno é `"Registro alterado com sucesso"`.

📌 **Pré-requisitos:**
- 🔹 Geração automática de um novo nome e sobrenome antes da requisição.

---

### **5️⃣ Deletar um usuário (`DELETE /usuarios/{{UserID}}`)**
- ✅ **Status Code 200** – Confirma que a exclusão foi bem-sucedida.
- ✅ **Resposta é um JSON válido** – Verifica a estrutura da resposta.
- ✅ **Mensagem de sucesso** – Confirma que a mensagem retornada é `"Registro excluído com sucesso"`.

---

## ⚡ Como executar os testes

1️⃣ **Instale as dependências (caso não tenha):**  
```sh
npm install -g newman newman-reporter-htmlextra
```

2️⃣ **Execute os testes e gere o relatório:**  
```sh
newman run ServeRest_API.postman_collection.json -e Env_ServeRest.postman_environment.json -r htmlextra
```

3️⃣ **Acesse o relatório gerado:**  
- O relatório estará na pasta `newman/`  
- Basta abrir o arquivo no navegador

