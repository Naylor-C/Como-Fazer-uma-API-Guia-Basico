# Como Fazer uma API: Guia Básico

Criar uma API (Application Programming Interface) é essencial para permitir que diferentes sistemas se comuniquem. Aqui está um guia básico para criar sua primeira API:

## 1. Escolha a Tecnologia

### Opções populares:
- **Node.js** (com Express)
- **Python** (com Flask ou Django REST Framework)
- **Java** (com Spring Boot)
- **PHP** (com Laravel)
- **C#** (com ASP.NET Core)

## 2. Estrutura Básica de uma API REST

```javascript
// Exemplo em Node.js com Express
const express = require('express');
const app = express();
const PORT = 3000;

// Middleware para parsear JSON
app.use(express.json());

// Rota GET básica
app.get('/api/hello', (req, res) => {
    res.json({ message: 'Olá Mundo!' });
});

// Inicia o servidor
app.listen(PORT, () => {
    console.log(`API rodando na porta ${PORT}`);
});
```

## 3. Principais Componentes

- **Rotas**: Definem os endpoints da API
- **Controladores**: Lógica de processamento das requisições
- **Modelos**: Estrutura dos dados
- **Middleware**: Funções intermediárias (autenticação, logs, etc.)

## 4. Boas Práticas

1. **Use padrão REST**:
   - GET para ler
   - POST para criar
   - PUT/PATCH para atualizar
   - DELETE para remover

2. **Versionamento**: `/api/v1/recursos`

3. **Documentação**: Use Swagger ou OpenAPI

4. **Tratamento de erros**: Códigos HTTP apropriados (200, 400, 404, 500)

5. **Segurança**:
   - HTTPS
   - Autenticação (JWT, OAuth)
   - Validação de entrada
   - Rate limiting

## 5. Exemplo Completo (Node.js/Express)

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

// Dados temporários (em produção, use um banco de dados)
let products = [
    { id: 1, name: 'Produto 1', price: 10.99 },
    { id: 2, name: 'Produto 2', price: 20.50 }
];

app.use(express.json());

// GET todos os produtos
app.get('/api/products', (req, res) => {
    res.json(products);
});

// GET produto por ID
app.get('/api/products/:id', (req, res) => {
    const product = products.find(p => p.id === parseInt(req.params.id));
    if (!product) return res.status(404).send('Produto não encontrado');
    res.json(product);
});

// POST criar novo produto
app.post('/api/products', (req, res) => {
    const product = {
        id: products.length + 1,
        name: req.body.name,
        price: req.body.price
    };
    products.push(product);
    res.status(201).json(product);
});

app.listen(PORT, () => {
    console.log(`API de produtos rodando na porta ${PORT}`);
});
```

## 6. Testando sua API

Use ferramentas como:
- Postman
- Insomnia
- curl (linha de comando)
- Testes automatizados (Jest, Mocha, etc.)

## 7. Próximos Passos

1. Conectar a um banco de dados (MongoDB, PostgreSQL, MySQL)
2. Implementar autenticação
3. Adicionar validação de dados
4. Escrever testes
5. Documentar com Swagger
6. Deploy em serviços como Heroku, AWS ou Azure

end;