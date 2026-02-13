# 🍜 Naruto 5D Web Store - Sistema de Vendas Automáticas

Bem-vindo à documentação técnica da loja oficial do servidor **Naruto 5D**. Este projeto consiste em uma plataforma web de alto desempenho desenvolvida para gerenciar a venda de vantagens (VIPs), itens e poderes para jogadores de Minecraft, com entrega totalmente automatizada.

---

## 🚀 Tecnologias Utilizadas

O projeto foi construído utilizando as tecnologias mais modernas do ecossistema Fullstack:

- **Frontend:** [Next.js 15](https://nextjs.org/) (App Router), Tailwind CSS, Lucide React.
- **Backend/Serveless:** [Next.js API Routes](https://nextjs.org/docs/app/building-your-application/routing/route-handlers).
- **Banco de Dados & Realtime:** [Supabase](https://supabase.com/) (PostgreSQL).
- **Gateways de Pagamento:** Mercado Pago (Brasil/BRL) e Stripe (Internacional/USD).
- **Envio de E-mails:** [Resend](https://resend.com/).
- **Hospedagem:** Vercel.

---

## 💎 Funcionalidades Principais

### 1. Detecção Inteligente de Localização
O sistema identifica automaticamente o país do usuário através do endereço IP. 
- **Brasileiros:** Visualizam preços em Reais (BRL) e utilizam o **Mercado Pago** (Pix/Cartão).
- **Estrangeiros:** Visualizam preços em Dólares (USD) e utilizam o **Stripe** (Cartão/Apple Pay/Google Pay).

### 2. Fábrica de Códigos Dinâmicos
Em vez de um estoque pré-carregado, desenvolvi um algoritmo de geração de hashes criptográficos que cria o código de resgate no momento exato da confirmação do pagamento (Webhook). Cada código contém um prefixo que identifica o item no servidor Minecraft.

### 3. Dashboard Realtime
Utilizando o recurso de **Realtime do Supabase**, o checkout monitora as mudanças no banco de dados via Webhook. Assim que o pagamento é aprovado, a interface do usuário atualiza instantaneamente para exibir o código gerado, sem necessidade de refresh.

### 4. Entrega via E-mail
Integração com a API Resend para envio automático de recibos e instruções de resgate com templates HTML profissionais.

---

## 📸 Demonstração Visual

| Home Page | Checkout Híbrido |
|---|---|
| <img src="./assets/home.png" width="400"> | <img src="./assets/checkout.png" width="400"> |

*(Adicione aqui um GIF de você comprando algo e o código aparecendo na tela)*

---

## 🛠️ Arquitetura do Sistema

1. **Pedido Iniciado:** O cliente escolhe o item e insere o e-mail.
2. **Gateway:** Requisição enviada via API para Mercado Pago ou Stripe.
3. **Webhook:** O gateway de pagamento notifica minha rota `/api/webhook`.
4. **Processamento:** O backend valida a assinatura do webhook, gera o código dinâmico e salva no banco.
5. **Entrega:** O código é exibido na tela do cliente em tempo real e enviado por e-mail via Resend.
6. **Resgate:** O jogador utiliza o comando `/resgatar <codigo>` dentro do servidor Minecraft.

---

## 🔒 Código Fonte
*Este projeto possui código fechado por razões de segurança e proteção de propriedade intelectual do servidor Naruto 5D. Esta documentação serve como demonstração técnica de habilidades em desenvolvimento Fullstack, integrações de APIs de pagamento e sistemas em tempo real.*

---
Desenvolvido por [Luan Neiva](https://github.com/LuaNeivA)
