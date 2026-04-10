#  EstoqueSM -> https://estoquesm.me

> Sistema SaaS de gestão de estoque integrado ao Mercado Livre, com controle de produtos, movimentações, vendas, chamados de suporte e painel administrativo.

---

##  Sobre o Projeto

O **EstoqueSM** é uma plataforma completa para pequenos e médios lojistas gerenciarem seu estoque de forma inteligente. Com integração nativa ao Mercado Livre, permite sincronizar produtos, acompanhar vendas e receber alertas de estoque baixo — tudo em um único lugar.

 **Produção:** [estoquesm.me](https://estoquesm.me)  
 **API:** [api.estoquesm.me](https://api.estoquesm.me)

---

##  Funcionalidades

- **Dashboard** — Visão geral de receita estimada, unidades vendidas, ticket médio e taxa de cancelamento
- **Produtos** — Cadastro, edição, categorização e controle de estoque por produto
- **Movimentações** — Histórico de entradas e saídas com rastreabilidade
- **Estoque Baixo** — Alertas automáticos de produtos abaixo do mínimo configurado
- **Integração Mercado Livre** — OAuth, publicação e atualização de anúncios, webhook de pedidos
- **Chamados de Suporte** — Sistema de tickets com upload de imagens, respostas do admin e controle de status
- **Painel Admin** — Gestão de usuários, chamados e notificações do sistema
- **Notificações do Sistema** — Avisos globais para todos os usuários com controle de expiração
- **Planos** — Diferenciação de funcionalidades por plano (Básico, Pro, Business)
- **Perfil** — Edição de dados pessoais, senha e preferências
- **Exportação de Extrato** — Geração de PDF com histórico de movimentações
- **Autenticação** — JWT com refresh token, verificação de e-mail e redefinição de senha

---

## Tecnologias

### Frontend
| Tecnologia | Uso |
|---|---|
| React 18 | Framework principal |
| Vite | Build tool |
| React Router | Navegação SPA |
| Axios | Requisições HTTP |
| PostHog | Analytics e rastreamento de eventos |
| Sentry | Monitoramento de erros frontend |
| Vercel | Deploy e hospedagem |

### Backend
| Tecnologia | Uso |
|---|---|
| Java 17 | Linguagem principal |
| Spring Boot 3.3 | Framework web |
| Spring Security | Autenticação e autorização |
| Spring Data JPA | ORM e acesso ao banco |
| Hibernate | Mapeamento objeto-relacional |
| JWT (jjwt) | Tokens de autenticação |
| Bucket4j | Rate limiting |
| iTextPDF | Geração de PDFs |
| SendGrid | Envio de e-mails transacionais |
| Sentry | Monitoramento de erros backend |
| AWS SDK S3 | Upload de imagens para Cloudflare R2 |

### Banco de Dados
| Tecnologia | Uso |
|---|---|
| MySQL | Banco principal |
| HikariCP | Pool de conexões |

### Infraestrutura
| Tecnologia | Uso |
|---|---|
| DigitalOcean VPS | Hospedagem do backend |
| Cloudflare R2 | Armazenamento de imagens (zero egress) |
| GitHub Actions | CI/CD — build e deploy automático |
| systemd | Gerenciamento do serviço Java na VPS |
| Nginx (via domínio) | Proxy reverso |

### Integrações Externas
| Integração | Uso |
|---|---|
| Mercado Livre API | OAuth, anúncios, webhooks de pedidos |
| SendGrid | E-mails de verificação, redefinição de senha |
| PostHog | Analytics de produto |
| Sentry | Error tracking frontend e backend |
| Cloudflare R2 | Storage de imagens dos chamados |

---



## Deploy

### Backend (Automático via GitHub Actions)

Todo `git push` na branch `main` dispara automaticamente:

1. Build do JAR com Maven
2. Envio via SCP para a VPS
3. Restart do serviço systemd

```yaml
# .github/workflows/deploy.yml
on:
  push:
    branches: [main]
```

### Frontend (Automático via Vercel)

O Vercel detecta o push e faz o deploy automaticamente.

### Deploy Manual (legado)

```bash
deploy.bat
```

---

## 🔧 Rodando Localmente

### Backend

```bash
./mvnw spring-boot:run
```

### Frontend

```bash
cd estoqueSM-front
npm install
npm run dev
```

---

## Monitoramento

- **Sentry** — Erros em produção (frontend + backend) em tempo real
- **PostHog** — Analytics de uso, pageviews e eventos customizados
- **Cloudflare R2** — Métricas de uso de storage e operações

---

##  Segurança

- Autenticação via JWT com blacklist de tokens
- Rate limiting por IP com Bucket4j
- Validação de magic bytes em uploads de imagem
- Variáveis sensíveis via `.env` e GitHub Secrets
- CORS configurado por origem
- Dados sensíveis nunca logados

---

##  Licença

Projeto privado — todos os direitos reservados.

---

<div align="center">
  Desenvolvido por <strong>Pedro Mancini</strong>
</div>
