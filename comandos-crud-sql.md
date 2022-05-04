# Comandos SQL para CRUD - Referência

## Resumo 
- C -> Create (inserir dados)
- R -> Read (ler dados)
- U -> Update (atualizar dados)
- D -> Delete (excluir dados)

## INSERT
```sql
INSERT INTO fabricantes (nome) VALUES ('Asus');
INSERT INTO fabricantes (nome) VALUES ('Dell');
INSERT INTO fabricantes (nome) VALUES ('Apple'), ('LG'), ('Samsung'), ('Brastemp');
```

### Produtos
```sql
INSERT INTO produtos(nome, descricao, preco,quantidade, fabricante_id) VALUES(
    'Ultrabook',
    'Ultrabook Asus com processador Intel Core i12, memória RAM de 16GB e Windows 11',
     6500.99,
     7,
     1 # Asus
);
```
```sql
INSERT INTO produtos(nome, descricao, preco,quantidade, fabricante_id) VALUES(
    'Tablet Android',
    'Tablet com a versão 12 do sistema operacional da Google, possui tela de 10 polegadas e armazenamento de 64 GB.',
     4999,
     3,
     5 # samsung
);
```
```sql
INSERT INTO produtos(nome, descricao, preco,quantidade, fabricante_id) VALUES
  (
      'Geladeira',
      'Refrigerador Frost-free com acesso pelo celular',
      1500,
      10,
      6 # Brastemp
  ),
  (
      'Iphone Pro Max',
      'Alta durabilidade, processador Bionic 14, 128 GB de armazenamento, 6GB de RAM e caro pra caramba',
      6999.99,
      3,
      3 # Apple
  ),
  (
      'Ipad Mini',
      'Tablet Apple com tela retina display de 4k, memória interna de 64 GB, acesso ao icloud.',
      5000,
      8,
      3 # Apple
  ),
);
```

```sql
INSERT INTO fabricantes (nome) VALUES ('Positivo'), ('Microsoft');
```

```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id) VALUES(
    'X-box',
    'Console de última geração com acesso aos melhores jogos',
    2500,
    6,
    8 # microsoft
),
(
    'Ultrabook',
    'Equipamento com processador AMD Ryzen5, 12GB de RAM, placa de vídeo RTX',
    4500.68,
    12,
    7 # Positivo
);
```


## SELECT

### Ler dados da tabela Produtos
```sql
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;

SELECT nome FROM produtos WHERE preco < 5000;

SELECT nome, descricao FROM produtos
WHERE fabricante_id = 3; # Apple
```

## Operadores Lógicos: E OU 

### Filtros
```sql
SELECT nome, preco FROM produtos ORDER BY nome; -- ASC (ordem padrão crescente)

SELECT nome, preco FROM produtos ORDER BY nome DESC; 

SELECT nome, descricao FROM produtos WHERE descricao LIKE '%processador%'; -- LIKE (COMO)

-- % Operador coringa (Significa qualquer texto)
```

### Operações e Funções de agregação
```sql
SELECT SUM(preco) FROM produtos; -- SUM (SOMA)

SELECT SUM(preco) AS total -- ALIAS(APELIDO)
FROM produtos;

SELECT SUM(quantidade) AS "Quantidade em Estoque"
FROM produtos;

SELECT SUM(quantidade) AS "Quantidade em Estoque"
FROM produtos WHERE fabricante_id = 3; -- Apple

-- AVG (AVERAGE) MÉDIA
SELECT AVG(preco) AS "Média dos Preços"
FROM produtos;

-- ROUND (Arredondamento)
SELECT ROUND(AVG(preco)) AS "Média dos Preços"
FROM produtos;

SELECT COUNT(id) AS "Quantidade de produtos"
FROM produtos;

-- DISTINCT (comando para evitar a repetição na contagem em campos que não são chave primária)
SELECT COUNT(DISTINCT fabricante_id) AS "Qtd de fabricantes"
FROM produtos;

INSERT INTO produtos (id, nome, descricao, preco, quantidade, fabricante_id) VALUES (NULL, 'Teclado Gamer', 'Teclado de última geração com teclas mecânicas e ótimo tempo de resposta com led embutido.', 380, 8, 8), (NULL, 'Placa-mãe', 'Placa com diversos slots de memória ram muito top bem rápido muito louco do caramba', 1200, 5, 1)

SELECT nome, preco, quantidade, (preco * quantidade) AS TOTAL
FROM produtos;
```

### Agrupamentos 
```sql
SELECT nome, fabricante_id, SUM(preco) AS Total From produtos
GROUP BY fabricante_id;
-- GROUP BY permite segmentar resultados de consulta. Neste caso, somamos todos os preços e segmentamos/agrupamos por cada fabricante
```



