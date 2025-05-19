# waha-n8n

waha-n8n é uma solução para orquestração de fluxos de mensagens WhatsApp usando n8n e WAHA.  
Permite receber eventos via webhook, processar mensagens com agentes de IA (Groq + LangChain)  
e responder automaticamente via WAHA.

## 📋 Pré-requisitos

- Docker & Docker Compose
- Conta WAHA com sessão configurada
- Acesso a Redis e Postgres (via Docker Compose)

## 🚀 Instalação e execução

1. Clone este repositório:
   ```bash
   git clone https://seu-repo.git
   cd n8n-waha
   ```
2. Inicie os serviços:
   ```bash
   docker-compose up -d
   ```
3. Acesse o n8n em `http://localhost:5678` e importe o workflow `Boot_Whatsapp.json`.

## 🔧 Serviços

- **n8n**: Automação de fluxos de trabalho (porta 5678)
- **WAHA**: Conexão com WhatsApp (porta 3000)
- **Redis**: Armazenamento de sessões e memória (porta 6379)
- **Postgres**: Banco de dados auxiliar (porta 5432)

## 🛠️ Uso

- Configure o webhook do WAHA para `http://n8n:5678/webhook/webhook`.
- Ajuste as variáveis de ambiente em `docker-compose.yml` conforme necessário.
- No n8n, modifique o node “AI Agent” para apontar ao seu modelo Groq/GPT.

## 📂 Estrutura de diretórios

```
n8n-waha/
├── Boot_Whatsapp.json   # Workflow n8n
├── README.md            # Documentação do projeto
├── docker-compose.yml   # Orquestração de containers
└── .sessions/           # Armazenamento de sessões WAHA (bind mount)
```

## 🤝 Contribuição

1. Fork do repositório.
2. Crie uma branch com sua feature: `git checkout -b feature/nova-funcionalidade`
3. Commit e push:  
   ```bash
   git commit -m "Descrição da mudança"
   git push origin feature/nova-funcionalidade
   ```
4. Abra um Pull Request explicando sua contribuição.

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
