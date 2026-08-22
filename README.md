# API REST – Café Aurora
Atividade Prática de Desenvolvimento Web Back-End (UNINTER)
Aluna: Eloise Bellorio – RU: 4951705

## O que é este projeto
API REST em Java + Spring Boot + Spring Data JPA, com as entidades **Cliente**, **Produto**
e **Pedido**, seguindo o padrão MVC do Spring. Usa banco **H2** (relacional, em arquivo
local) — não precisa instalar MySQL para funcionar.

---

## PASSO 1 — Importar no Eclipse

1. Abra o Eclipse.
2. Vá em **File > Import... > Maven > Existing Maven Projects**.
3. Em "Root Directory", clique em **Browse** e selecione a pasta `cafe-aurora-api`
   (a pasta que contém o arquivo `pom.xml`).
4. Clique em **Finish**. O Eclipse vai baixar as dependências automaticamente
   (pode levar 1-2 minutos na primeira vez — precisa de internet).

> Se preferir, pode usar o **Spring Tool Suite (STS)** ou o **IntelliJ** também —
> o processo de importar projeto Maven é parecido.

## PASSO 2 — Rodar a aplicação

1. No Eclipse, abra o arquivo:
   `src/main/java/com/cafearora/api/CafeAuroraApiApplication.java`
2. Clique com o botão direito nele → **Run As > Java Application**.
3. Aguarde até aparecer no console algo como:
   `Tomcat started on port(s): 8080`
4. Pronto! A API está rodando em `http://localhost:8080`

## PASSO 3 — Testar no Postman

Abra o Postman e envie as seguintes requisições, na ordem (isso cobre todos os
testes obrigatórios do trabalho). Tire um **print de cada uma** e cole no documento
Word, na seção 4:

### 1. Criar Cliente
- Método: `POST`
- URL: `http://localhost:8080/clientes`
- Body → raw → JSON:
```json
{
  "nome": "EloiseBellorio4951705",
  "clienteDesde": "2026-08-22"
}
```

### 2. Criar Produto
- Método: `POST`
- URL: `http://localhost:8080/produtos`
- Body → raw → JSON:
```json
{
  "nome": "Café Bourbon Amarelo 250g",
  "preco": 32.90,
  "estoque": true
}
```

### 3. Criar Pedido
- Método: `POST`
- URL: `http://localhost:8080/pedidos`
- Body → raw → JSON (troque os IDs pelos que vieram nas respostas anteriores,
  provavelmente `1` e `1` se for o primeiro cliente/produto cadastrado):
```json
{
  "clienteId": 1,
  "produtoId": 1,
  "quantidade": 3
}
```

### 4. Listagem geral
- `GET http://localhost:8080/clientes`
- `GET http://localhost:8080/produtos`
- `GET http://localhost:8080/pedidos`

### 5. Consulta por ID
- `GET http://localhost:8080/clientes/1`

### 6. Apagar (DELETE)
- `DELETE http://localhost:8080/clientes/1` (ou produto/pedido, à sua escolha)
- Resposta esperada: `204 No Content`

---

## PASSO 4 — Subir para o GitHub

1. Crie um repositório novo no GitHub (pode ser público), ex: `cafe-aurora-api`.
2. No Eclipse: botão direito no projeto → **Team > Share Project > Git** → crie um
   repositório local.
3. Depois: botão direito → **Team > Commit...** → selecione todos os arquivos → escreva
   uma mensagem (ex: "Projeto Café Aurora - Atividade Prática") → **Commit**.
4. Depois: **Team > Remote > Push...** → cole a URL do repositório criado no GitHub → **Push**.

Ou, se preferir pelo terminal, dentro da pasta `cafe-aurora-api`:
```bash
git init
git add .
git commit -m "Projeto Café Aurora - Atividade Pratica"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/cafe-aurora-api.git
git push -u origin main
```

Copie o link do repositório e cole no documento Word, na seção 5.

---

## Estrutura do projeto
```
cafe-aurora-api/
├── pom.xml
└── src/main/
    ├── java/com/cafearora/api/
    │   ├── CafeAuroraApiApplication.java
    │   ├── model/       (Cliente, Produto, Pedido)
    │   ├── repository/  (ClienteRepository, ProdutoRepository, PedidoRepository)
    │   └── controller/  (ClienteController, ProdutoController, PedidoController)
    └── resources/
        └── application.properties
```
