# Naruto 5D Web Store

Documentação técnica da plataforma oficial de vendas do servidor **Naruto 5D**. Este projeto é um e-commerce fullstack desenvolvido para gerenciar transações automatizadas de itens digitais para Minecraft, com suporte a pagamentos nacionais e internacionais.

---

## Link do Projeto
O sistema está em operação e pode ser acessado em:  
[https://www.naruto5d.com.br](https://www.naruto5d.com.br)

---

## Visão Geral
A Naruto 5D Web Store foi projetada para solucionar o desafio de entrega instantânea de produtos in-game. O sistema automatiza todo o fluxo: desde a detecção da moeda local do usuário até a geração dinâmica de chaves criptográficas de resgate após a confirmação do pagamento.

---

## Tecnologias Utilizadas

### Core
- **Frontend:** Next.js 15 (App Router) & React 19
- **Linguagem:** TypeScript
- **Estilização:** Tailwind CSS 4

### Infraestrutura e Backend
- **Banco de Dados:** Supabase (PostgreSQL)
- **Realtime:** Supabase Channels (Websockets)
- **E-mail Transacional:** Resend API

### Gateways de Pagamento
- **Brasil (BRL):** Mercado Pago (Integração com Pix e Checkout Transparente)
- **Internacional (USD):** Stripe (Suporte a Apple Pay, Google Pay e Cartões Globais)

---

## Arquitetura e Diferenciais Técnicos

### Localização Dinâmica
O sistema implementa uma camada de geolocalização via IP que ajusta automaticamente a interface. Usuários brasileiros acessam o fluxo em Reais via Mercado Pago, enquanto usuários estrangeiros são direcionados ao fluxo em Dólares via Stripe, otimizando as taxas de conversão.

### Fábrica de Códigos (Code Factory)
Para garantir segurança e estoque infinito, o sistema não utiliza códigos pré-gerados. Desenvolvi um algoritmo que, no momento da confirmação do pagamento (via Webhook), gera um hash único baseado no tipo de produto e timestamp. Esse código é atrelado à transação e enviado simultaneamente para a interface do usuário e para o e-mail cadastrado.

### Sincronização em Tempo Real
A interface de checkout utiliza listeners do Supabase para monitorar alterações no banco de dados. Assim que o webhook do provedor de pagamento processa a transação, a tela do cliente é atualizada instantaneamente com o código de resgate, eliminando a necessidade de atualização manual da página.

---

## Fluxo de Operação

1. **Checkout:** O usuário informa o e-mail e o sistema valida a moeda baseada na localização.
2. **Processamento:** A transação é enviada ao gateway (Mercado Pago ou Stripe).
3. **Confirmação:** O gateway dispara uma notificação assíncrona (Webhook) para a API da loja.
4. **Entrega:** O backend valida a assinatura do webhook, gera o código de resgate dinâmico, registra o pedido no banco de dados e dispara o e-mail transacional via Resend.
5. **Interface:** O código é exibido em tempo real na tela final do checkout.

---

## Demonstração Visual

| Catálogo de Produtos | Checkout Inteligente | Entrega Realtime |
|---|---|---|
| <img src="./assets/home.png" width="300"> | <img src="./assets/checkout.png" width="300"> | <img src="./assets/sucesso.png" width="300"> |

---

## Segurança e Privacidade
O código-fonte deste projeto é mantido de forma privada para proteger a lógica proprietária de geração de chaves e a integridade do servidor Naruto 5D. Este repositório serve como portfólio técnico, demonstrando expertise em arquitetura fullstack, integrações financeiras e sistemas realtime.

---
**Desenvolvido por Luan Neiva**  
[GitHub Profile](https://github.com/LuaNeivA)
