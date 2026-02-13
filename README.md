<div align="center">
  <img src="./assets/logo.png" width="250" alt="Naruto 5D Logo">
  <h1>Naruto 5D Web Store</h1>
</div>

Documentação técnica da plataforma oficial de vendas do servidor **Naruto 5D**. Este projeto consiste em um ecossistema fullstack desenvolvido para gerenciar transações automatizadas de itens digitais e vantagens in-game para Minecraft.

---

## Link do Projeto
O sistema está em operação e pode ser acessado em:  
[https://www.naruto5d.com.br](https://www.naruto5d.com.br)

---

## Visão Geral
A Naruto 5D Web Store foi projetada para automatizar o ciclo completo de venda e entrega de produtos digitais. A aplicação resolve desafios críticos de e-commerce, como a detecção dinâmica de moeda baseada em geolocalização e a geração de chaves criptográficas de uso único no momento da confirmação do pagamento.

---

## Tecnologias Utilizadas

### Frontend e Interface
- **Next.js 15 (App Router):** Framework principal para renderização híbrida e performance.
- **React 19:** Utilização de hooks avançados para gerenciamento de estado e contexto.
- **Tailwind CSS 4:** Estilização baseada em design tokens e responsividade extrema.

### Infraestrutura e Backend
- **Supabase (PostgreSQL):** Persistência de dados e gerenciamento de banco de dados relacional.
- **Supabase Realtime:** Implementação de WebSockets para atualização instantânea da interface.
- **Resend API:** Infraestrutura para envio de e-mails transacionais com alta taxa de entregabilidade.

### Gateways de Pagamento
- **Mercado Pago (BRL):** Integração para o mercado nacional com foco em aprovação via Pix.
- **Stripe (USD):** Solução para o mercado internacional com suporte a cartões globais, Apple Pay e Google Pay.

---

## Diferenciais Técnicos

### Inteligência de Geolocalização
O sistema implementa uma camada de middleware que identifica a origem do tráfego via IP. Essa lógica ajusta automaticamente a exibição dos preços (Real ou Dólar) e renderiza o gateway de pagamento mais adequado para a região do usuário, otimizando as taxas de conversão globais.

### Arquitetura Code Factory
Para eliminar a necessidade de estoques manuais, desenvolvi um algoritmo de geração dinâmica. No momento em que o Webhook do gateway confirma a transação, o backend processa o `type_id` do produto e gera um hash único. Este código é registrado no banco de dados e entregue ao usuário em milissegundos.

### Sincronização Realtime de Pedidos
A página de checkout opera como uma Single Page Application (SPA) que escuta eventos do banco de dados. Através de canais de broadcast do Supabase, o cliente recebe o feedback visual do pagamento e o código de resgate sem a necessidade de atualizar a página ou realizar requisições manuais de status.

---

## Fluxo de Operação

1. **Checkout:** O usuário informa o e-mail de recebimento e o sistema valida a moeda local.
2. **Processamento:** A requisição de pagamento é enviada de forma segura ao provedor (Stripe ou Mercado Pago).
3. **Webhook:** O gateway envia uma notificação assinada para a rota de API da aplicação.
4. **Fulfillment:** O servidor valida a assinatura, gera o código de resgate, registra a ordem e dispara o e-mail via Resend.
5. **Entrega:** O componente de checkout detecta a mudança de status via WebSocket e exibe o código na tela.

---

## Demonstração Visual

| Catálogo de Produtos | Checkout Híbrido | Entrega do Código |
|---|---|---|
| <img src="./assets/home.png" width="300"> | <img src="./assets/checkout.png" width="300"> | <img src="./assets/sucesso.png" width="300"> |

---

## Segurança e Propriedade Intelectual
O código-fonte deste projeto é mantido sob sigilo para proteger a lógica proprietária de geração de chaves e a integridade do servidor Naruto 5D. Este repositório cumpre a função de documentação técnica para demonstração de competências em desenvolvimento de sistemas financeiros, arquitetura fullstack e integrações realtime.

---
**Desenvolvido por Luan Neiva**  
[GitHub Profile](https://github.com/LuaNeivA)
