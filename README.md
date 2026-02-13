# 🍜 Naruto 5D Web Store - E-commerce de Alta Performance

<div align="center">
  <img src="./assets/logo.png" width="200" alt="Naruto 5D Logo">
  <br />
  <a href="https://www.naruto5d.com.br">
    <img src="https://img.shields.io/badge/Acessar_Loja_Ao_Vivo-FF9900?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Live Site">
  </a>
  <img src="https://img.shields.io/badge/Status-Em_Produção-4ade80?style=for-the-badge" alt="Status">
</div>

---

## 🔗 Link Oficial do Projeto
O sistema está em operação real e pode ser acessado em:  
👉 **[https://www.naruto5d.com.br](https://www.naruto5d.com.br)**

---

## 📝 Sobre o Projeto
Esta é a plataforma oficial de vendas do servidor **Naruto 5D**. O projeto foi desenvolvido para oferecer uma experiência de compra fluida, segura e totalmente automatizada para jogadores de Minecraft no Brasil e no exterior.

A aplicação resolve o desafio de vender itens digitais com **entrega instantânea**, integrando múltiplos gateways de pagamento e um sistema de geração dinâmica de chaves de resgate.

---

## 🚀 Stack Tecnológica

O ecossistema do projeto utiliza as tecnologias mais modernas para garantir escalabilidade e tempo de resposta imediato:

- **Frontend:** [Next.js 15](https://nextjs.org/) (App Router & React 19).
- **Estilização:** [Tailwind CSS 4](https://tailwindcss.com/) com design responsivo e efeitos de Glow/Glassmorphism.
- **Backend/API:** Next.js Serverless Functions.
- **Banco de Dados:** [Supabase](https://supabase.com/) (PostgreSQL).
- **Comunicação Realtime:** Supabase Channels (Websockets para atualização de checkout).
- **Gateways de Pagamento:** 
  - **Brasil:** Mercado Pago (Pix com aprovação imediata).
  - **Internacional:** Stripe (Cartões, Apple Pay e Google Pay).
- **E-mail Transacional:** [Resend](https://resend.com/) com templates em React Email.

---

## 💎 Diferenciais Técnicos

### 1. Checkout Híbrido & Geolocalização
O sistema detecta automaticamente a origem do usuário via IP. 
- Jogadores brasileiros veem preços em **BRL** e pagam via Pix. 
- Jogadores internacionais veem preços em **USD** e utilizam o Stripe, garantindo a menor taxa de conversão e maior facilidade global.

### 2. Fábrica de Códigos Dinâmicos (Anti-Fraude)
Diferente de lojas comuns, este sistema não trabalha com "estoque de chaves". Utilizei uma lógica de **Code Factory** que gera um hash criptográfico único no momento do Webhook de confirmação. Isso impede o esgotamento de itens e garante que cada código seja atrelado a uma transação verificada.

### 3. Sincronização em Tempo Real
A página de checkout não precisa de atualização manual. Implementei um listener de banco de dados (Realtime) que monitora o status do pedido. Assim que o Webhook do gateway confirma o pagamento, o código de resgate aparece instantaneamente na tela do cliente.

### 4. Entrega Multicanal
O código gerado é entregue em três frentes:
1. Interface do site (Realtime).
2. E-mail formatado (HTML profissional via Resend).
3. Banco de dados (Histórico de pedidos).

---

## 🛠️ Arquitetura de Fluxo

1. **Seleção:** Jogador escolhe um item (Ex: VIP ou Skilltree).
2. **Checkout:** Inserção de e-mail e detecção automática de moeda.
3. **Pagamento:** Processamento via Mercado Pago ou Stripe.
4. **Webhook:** O gateway notifica a API da loja.
5. **Lógica de Entrega:** O servidor valida o pagamento, chama o `codeGenerator`, salva no banco e dispara o e-mail.
6. **Interface:** O cliente recebe o código na tela sem dar F5.

---

## 📸 Demonstração

| Página Inicial (Catálogo) | Checkout Inteligente | Entrega do Código |
|---|---|---|
| <img src="./assets/home.png" width="300"> | <img src="./assets/checkout.png" width="300"> | <img src="./assets/sucesso.png" width="300"> |

---

## 🔒 Informação sobre o Código Fonte
Por questões de segurança e confidencialidade, o código-fonte deste projeto é **privado**. Esta página serve como portfólio técnico para demonstrar proficiência em:
- Integração complexa de APIs financeiras.
- Gerenciamento de estado e arquitetura Fullstack.
- Segurança em Webhooks e processamento de dados sensíveis.
- UI/UX focada em conversão para o público gamer.

---
**Desenvolvido por [Luan Neiva](https://github.com/LuaNeivA)**  
*Especialista em soluções Fullstack e Modelagem 3D.*
