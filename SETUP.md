# Guia Completo de Configuração

## 📋 Pré-requisitos

- Python 3.8 ou superior
- Conta do Google Cloud
- Acesso ao Google Drive

## 🔧 Passo 1: Configurar Google Cloud

### 1.1 Criar Projeto no Google Cloud Console

1. Acesse [Google Cloud Console](https://console.cloud.google.com/)
2. Clique em "Selecionar um projeto" no topo
3. Clique em "NOVO PROJETO"
4. Digite o nome: `Assinador PDF Envolver`
5. Clique em "CRIAR"

### 1.2 Ativar Google Drive API

1. No Google Cloud Console, vá para "APIs e Serviços"
2. Clique em "Habilitar APIs e serviços"
3. Procure por "Google Drive API"
4. Clique nela e depois em "ATIVAR"

### 1.3 Criar Service Account

1. No Google Cloud Console, vá para "Credenciais"
2. Clique em "Criar credenciais" → "Service account"
3. Preencha:
   - Nome da conta de serviço: `assinador-pdf`
   - ID da conta de serviço: (preenchido automaticamente)
4. Clique em "CRIAR E CONTINUAR"
5. Clique em "CONTINUAR" (etapas 2 e 3 são opcionais)
6. Clique em "CONCLUÍDO"

### 1.4 Gerar Chave JSON

1. Clique na conta de serviço criada
2. Vá para a aba "Chaves"
3. Clique em "Adicionar chave" → "Criar nova chave"
4. Escolha "JSON"
5. Clique em "CRIAR"
6. Um arquivo JSON será baixado - **salve em local seguro**

## 💾 Passo 2: Configurar Streamlit

1. Clone ou baixe este repositório
2. Crie a pasta `.streamlit`:
   ```bash
   mkdir .streamlit
   ```

3. Crie o arquivo `.streamlit/secrets.toml`:
   ```toml
   [gcp_service_account]
   type = "service_account"
   project_id = "seu-projeto-id"
   private_key_id = "sua-chave-id"
   private_key = "-----BEGIN PRIVATE KEY-----\nconteudo-da-chave\n-----END PRIVATE KEY-----\n"
   client_email = "assinador-pdf@seu-projeto.iam.gserviceaccount.com"
   client_id = "seu-client-id"
   auth_uri = "https://accounts.google.com/o/oauth2/auth"
   token_uri = "https://oauth2.googleapis.com/token"
   auth_provider_x509_cert_url = "https://www.googleapis.com/oauth2/v1/certs"
   client_x509_cert_url = "https://www.googleapis.com/robot/v1/metadata/x509/assinador-pdf@seu-projeto.iam.gserviceaccount.com"
   ```

4. Substitua os valores com os dados do arquivo JSON baixado

## 🚀 Passo 3: Instalar Dependências

```bash
pip install -r requirements.txt
```

## 📁 Passo 4: Compartilhar Pasta do Google Drive

1. Crie uma pasta no Google Drive (ex: "Documentos para Assinar")
2. Clique com botão direito → "Compartilhar"
3. Cole o email do Service Account: `assinador-pdf@seu-projeto.iam.gserviceaccount.com`
4. Dê permissão de "Editor"
5. Clique em "Compartilhar"

## ▶️ Passo 5: Executar a Aplicação

```bash
streamlit run app.py
```

A aplicação abrirá automaticamente em `http://localhost:8501`

## ✅ Testando

1. Coloque um PDF na pasta compartilhada do Google Drive
2. Selecione a pasta e o PDF
3. Clique em "Carregar PDF"
4. Desenhe sua assinatura
5. Clique em "Assinar e Salvar"

## 🐛 Troubleshooting

### Erro: "Please set your GCP service account key"
- Verifique se o arquivo `.streamlit/secrets.toml` existe
- Verifique se as credenciais estão corretas

### Erro: "No folders found in Google Drive"
- Verifique se a pasta foi compartilhada com o email do Service Account
- Verifique se a permissão é de "Editor"

### Erro ao baixar PDF
- Verifique se o PDF está na pasta compartilhada
- Verifique a conexão com a internet

### Erro ao fazer upload
- Verifique se há espaço no Google Drive
- Verifique as permissões da pasta

## 📞 Suporte

Para mais informações, acesse a documentação oficial:
- [Google Cloud Documentation](https://cloud.google.com/docs)
- [Google Drive API](https://developers.google.com/drive)
- [Streamlit Documentation](https://docs.streamlit.io/)
