# ecommerce-backend

  esse sistema é um backend de um e-commerce, onde é possível realizar cadastro de usuários, produtos,  categorias, endereços, pedidos e itens do pedido.


## MODELO DE DADOS
## Entidades principais:

- ###  Usuários (U): Armazena informações sobre os clientes do e-commerce, como nome completo, email, senha, telefone e endereço padrão.
- ### Endereços (A): Registra os endereços de entrega dos clientes.
- ### Produtos (P): Contém informações sobre os produtos vendidos, como nome, descrição, preço, estoque, imagem e status.
- ### Pedidos (O): Armazena dados sobre os pedidos realizados pelos clientes, como data do pedido, status, endereço de entrega, método de pagamento e total do pedido.
- ### Itens do Pedido (IO): Detalha os produtos de cada pedido, incluindo quantidade, preço e total do item.
## Entidades complementares:

- ### Categorias (C): Classifica os produtos em diferentes categorias, facilitando a navegação na loja virtual.
- ### Produto-Categoria (PC): Estabelece a relação entre produtos e categorias, permitindo que um produto pertença a mais de uma categoria.
- ### Vendas de Produtos (PS): Registra as vendas de cada produto, com quantidade vendida e data da venda.
- ### Estoque Disponível (AS): Informa a disponibilidade de cada produto, com a quantidade em estoque, avaliação e comentários dos clientes.
- ### Carrinho de Compras (SC): Armazena os produtos que os clientes adicionaram ao carrinho, mas ainda não finalizaram a compra.
- ### Produto do Carrinho de Compras (SCP): Detalha os produtos no carrinho de compras, incluindo quantidade.

## Regras de Negócio

### Entidade: Users (U)

- Histórico de compras: Registrar o histórico de compras de cada usuário para análise e personalização de ofertas.
- Política de senha: Definir requisitos de força para a senha (tamanho mínimo, caracteres especiais, etc.).
-Verificação de email: Enviar um email de verificação para confirmar o endereço de email cadastrado
- Recuperação de senha: Permitir que o usuário redefina a senha por meio de um link enviado por email.
- Perfil do usuário: Permitir que o usuário edite suas informações pessoais e endereços cadastrados.
- Exclusão de conta: Permitir que o usuário exclua sua conta

#### Cadastro:
- O usuário deve preencher todos os campos obrigatórios (nome completo, email, senha, 
- telefone) para se cadastrar.
- O email deve ser único e válido.
- A senha deve ser criptografada com um algoritmo seguro (como bcrypt).
- O telefone deve ser único e válido.
- 
#### Login:
- O email e a senha informados devem corresponder a um usuário cadastrado.
- Implementar políticas de tentativas de login para evitar ataques de força bruta.

### Entidade: Address (A)

- Limite de endereços: Definir se há um limite para o número de endereços que um usuário pode cadastrar.
- Endereço padrão: Um usuário deve ter um endereço padrão definido para entregas.
- Validação de endereço: Verificar se o endereço fornecido é válido (CEP, formato, etc.).
- Exclusão de endereço: Permitir que o usuário exclua endereços cadastrados.
- Relacionamento: Um endereço pertence a um único usuário, e um usuário pode ter vários endereços (um para muitos).

### Entidade: Product (P)

- Preço: O preço e o preço de atacado devem ser valores positivos.
- Disponibilidade: A quantidade de estoque disponível deve ser um valor não negativo.
- Imagens: Definir o tamanho máximo permitido para as imagens dos produtos.
- Status: O status do produto deve ser "outStock" ou "inStock".

### Entidade: Order (O)

- Status do pedido: O status do pedido deve refletir o fluxo de processamento (pendente, em processamento, enviado, entregue, cancelado).
- Total do pedido: O total do pedido deve ser calculado com base na quantidade e preço dos itens comprados, considerando descontos de cupons (se houver).
- Validação de endereço de entrega: O endereço de entrega deve pertencer ao cliente que realizou o pedido.
- Validação do método de pagamento: O método de pagamento selecionado deve ser válido e suportado pelo e-commerce.
- Cancelamento de pedido: Permitir que o cliente cancele um pedido antes do envio.

### Entidade: ItemOrder (IO)

- Quantidade: A quantidade de itens por produto no pedido deve ser um valor positivo.
### Entidade: Categories (C)

- Nome da categoria: O nome da categoria deve ser único e descritivo.
- 
### Entidade: ProductCategory (PC)

- Relacionamento: Um produto pode pertencer a várias categorias, e uma categoria pode conter vários produtos (muitos para muitos).

### Entidade: ProductSales (PS)

- Quantidade vendida: A quantidade vendida deve ser um valor positivo e não pode exceder a quantidade disponível em estoque.
### Entidade: Available_Stock (AS)

- Avaliação: A avaliação por estrelas deve estar entre 0 e 5.
- Comentários: Permitir que os clientes deixem comentários sobre os produtos.
- 
### Entidade: ShoppingCart (SC)

- Limite de itens: Definir se há um limite para o número de itens que um cliente pode adicionar ao carrinho.
- Exclusão de itens: Permitir que o cliente exclua itens do carrinho.
- 
### Entidade: ShoppingCartProduct (SCP)

- Quantidade: A quantidade de itens por produto no carrinho deve ser um valor positivo.
### Entidade: Coupons (CP)

- Validade: O cupom deve ter uma data de expiração.
- Tipo de desconto: O tipo de desconto pode ser percentual ou valor fixo.
- Valor do desconto: O valor do desconto deve ser positivo (para descontos percentuais) ou não-negativo (para descontos fixos).
- Restrições de uso: Definir se há restrições de uso para o cupom (valor mínimo de compra, categorias específicas, etc.).

### Entidade: OrderCoupon (OCP)

- Relacionamento: Um pedido pode ter um único cupom associado.