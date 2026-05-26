# Assinador Drive Envolver

Uma aplicação Streamlit para assinar PDFs digitalmente e enviá-los diretamente para o Google Drive.

## Funcionalidades

- 🔐 Autenticação segura com Google Drive via Service Account
- 📁 Navegação de pastas do Google Drive
- 📄 Seleção e visualização de arquivos PDF
- ✍️ Canvas interativo para desenhar assinatura
- 💾 Merge da assinatura no PDF e upload automático
- 🔄 Backup automático do arquivo original

## Requisitos

- Python 3.8+
- Streamlit
- Google Cloud Service Account

## Instalação

```bash
pip install -r requirements.txt
```

## Configuração

1. Crie um Service Account no Google Cloud Console
2. Baixe as credenciais JSON
3. Configure as credenciais no Streamlit:
   - Crie `.streamlit/secrets.toml`:
   ```toml
   [gcp_service_account]
   type = "service_account"
   project_id = "seu-projeto"
   private_key_id = "..."
   # ... outras configurações
   ```

## Uso

```bash
streamlit run app.py
```

## Estrutura do Projeto

```
assinador-drive-envolver/
├── app.py                 # Aplicação principal
├── requirements.txt       # Dependências
├── .streamlit/
│   └── config.toml       # Configuração Streamlit
└── README.md
```

## Melhorias Implementadas

- ✅ Correção do bug de inserção de imagem (PyMuPDF)
- ✅ Melhor tratamento de erros
- ✅ Backup automático do arquivo original
- ✅ Limpeza de arquivos temporários mais robusta
- ✅ Logging e mensagens de usuário mais claras
- ✅ Documentação completa

## Licença

MIT
