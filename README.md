
README – Banco de Dados para Sistema de Delivery / Lanchonete
🍔 Sobre o Projeto

Este projeto representa o banco de dados de um sistema de delivery/lanchonete, modelado por meio de um Diagrama Entidade-Relacionamento (ER).
O objetivo é controlar clientes, atendentes, entregadores, pedidos e itens do cardápio de maneira organizada, garantindo rastreabilidade completa desde a realização do pedido até a entrega.

🧱 Entidades do Sistema

O banco é composto pelas seguintes entidades:

👤 1. clientes

Representa o cliente que faz o pedido.

Atributos

cpf (PK) – identifica o cliente

nome

pagamento

pedido

Relacionamento

clientes (1,1) realiza (0,n) pedido
Um cliente pode fazer vários pedidos; um pedido pertence a um único cliente.

🧑‍💼 2. atendente

Funcionário que registra o pedido no sistema.

Atributos

cpf (PK)

nome

qualificacoes

Relacionamento

atendente (1,n) efetua (1,1) pedido
Cada pedido é lançado por exatamente um atendente, e um atendente pode lançar vários pedidos.

🛵 3. entregador

Responsável por entregar o pedido ao cliente.

Atributos

id_pedido (PK)

nome

valor

pagamento

pedido

Relacionamento

entregador (1,n) realiza (0,1) pedido
Um entregador pode realizar várias entregas, mas cada pedido tem no máximo um entregador.

🧾 4. pedido

A entidade central do sistema.

Atributos

id (PK)

item

valor

Relacionamentos

Recebe um cliente: (1,1) cliente → pedido

É efetuado por um atendente: (1,n) atendente → pedido

Pode ser realizado por um entregador: (1,n) entregador → pedido

Contém itens do cardápio: (1,n) cardápio → pedido

🍽️ 5. cardápio

Itens disponíveis para venda (lanche, bebida, sobremesa etc.).

Atributos

id (PK)

item

valor

bebida

lanche

sobremesa

Relacionamento

cardápio (1,n) realiza (1,n) pedido
Um item do cardápio pode aparecer em vários pedidos, e um pedido pode conter vários itens → relação N:N representada pelo relacionamento realiza.

🔗 Relacionamentos Principais
✔ Cliente — Pedido
(1,1) clientes ----- realiza ----- (0,n) pedido

✔ Atendente — Pedido
(1,n) atendente ----- efetua ----- (1,1) pedido

✔ Entregador — Pedido
(1,n) entregador ----- realiza ----- (0,1) pedido

✔ Cardápio — Pedido
(1,n) cardápio ----- realiza ----- (1,n) pedido


Esse último representa uma relação Muitos-para-Muitos (N:N).

📊 Objetivo do Sistema

O banco foi projetado para:

cadastrar clientes e seus pedidos

permitir que atendentes registrem pedidos

registrar quais entregadores estão responsáveis por cada entrega

manter um cardápio organizado

armazenar valores e formas de pagamento

controlar todo o fluxo do pedido: pedido → preparo → entrega

🧠 Funcionamento Geral

O cliente faz um pedido.

O atendente registra esse pedido no sistema.

Cada pedido tem um ou mais itens do cardápio.

O entregador realiza a entrega e registra pagamento/valor.

Todo esse fluxo está modelado corretamente no diagrama ER.

🛠️ Possíveis Implementações Futuras

Criar tabela itens_do_pedido (para normalizar a relação entre pedido e cardápio).

Adicionar status do pedido (pendente, preparando, saiu pra entrega, entregue).

Cadastrar horários de entrada/saída de atendentes e entregadores.

Criar relatórios:

vendas por atendente

entregas por motoboy

itens mais vendidos

Criar interface web com CRUDs completos.

📦 Estrutura Resumida do Sistema
clientes (1,1)
  └── realiza ── (0,n) pedido ── efetua ── (1,n) atendente
                                   │
                                   └── realiza ── (1,n) entregador
                                   └── realiza ── (1,n) cardápio
