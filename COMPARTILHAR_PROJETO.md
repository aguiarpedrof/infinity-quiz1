# 📤 Como Compartilhar o Projeto TCC Infinity

Este guia explica como preparar e compartilhar o projeto com seu colega para que ele possa rodar no computador dele.

---

## 📋 Passo a Passo para VOCÊ (quem está enviando)

### 1️⃣ Exportar o Banco de Dados

```bash
cd backend
node export_db.js
```

**O que acontece:**
- ✅ Cria um arquivo `.sql` com todos os dados do banco
- ✅ Nome do arquivo: `infinity_quiz_backup_YYYY-MM-DD.sql`
- ✅ Inclui: tabelas, dados, usuários, perguntas, pontuações

**Saída esperada:**
```
🔄 Iniciando exportação do banco de dados...

📂 Banco: infinity_quiz
💾 Arquivo: C:\Users\pedro\Desktop\TCC_Infinity\backend\infinity_quiz_backup_2026-02-02.sql

✅ Banco de dados exportado com sucesso!

📊 Informações do arquivo:
   - Nome: infinity_quiz_backup_2026-02-02.sql
   - Tamanho: 156.42 KB
   - Localização: C:\Users\pedro\Desktop\TCC_Infinity\backend\infinity_quiz_backup_2026-02-02.sql

📤 Envie este arquivo .sql para seu colega junto com o projeto!
```

### 2️⃣ Preparar Arquivos para Envio

**Opção A: Compactar tudo (Recomendado)**

1. Vá até `C:\Users\pedro\Desktop\`
2. Clique com botão direito em `TCC_Infinity`
3. Enviar para → Pasta compactada
4. Resultado: `TCC_Infinity.zip`

**Opção B: Usar Git (se tiver repositório)**

```bash
# Seu colega clona o repositório
git clone <url-do-repositorio>
```

**⚠️ IMPORTANTE:** O arquivo `.sql` gerado está em `backend/`. Certifique-se de incluí-lo no ZIP!

### 3️⃣ Enviar para seu Colega

Envie os seguintes arquivos:
- ✅ `TCC_Infinity.zip` (projeto completo)
- ✅ `backend/infinity_quiz_backup_YYYY-MM-DD.sql` (já está dentro do ZIP)

**Formas de envio:**
- Google Drive
- WeTransfer
- OneDrive
- Pendrive
- Email (se for pequeno)

---

## 📥 Passo a Passo para SEU COLEGA (quem está recebendo)

### 1️⃣ Pré-requisitos

Seu colega precisa instalar:

#### Node.js (v18 ou superior)
- **Download:** https://nodejs.org/
- Escolher versão LTS
- Verificar instalação: `node --version`

#### MySQL Server (v8.0 ou superior)
- **Download:** https://dev.mysql.com/downloads/mysql/
- Durante instalação, anotar a **senha do root**
- Verificar instalação: `mysql --version`

**📝 Guia detalhado de instalação:** Ver arquivo `docs/DATABASE_SETUP.md`

### 2️⃣ Extrair o Projeto

1. Extrair `TCC_Infinity.zip` para uma pasta (ex: `C:\projetos\TCC_Infinity`)
2. Verificar se o arquivo `.sql` está em `backend/`

### 3️⃣ Configurar Variáveis de Ambiente

1. Abrir `backend/.env`
2. Ajustar a senha do MySQL:

```env
DB_HOST=localhost
DB_USER=root
DB_PASS="SUA_SENHA_DO_MYSQL"  # ← Trocar aqui!
DB_NAME=infinity_quiz
PORT=3000
```

**Exemplo:**
```env
DB_PASS="MinhaSenh@123"
```

### 4️⃣ Instalar Dependências

```bash
# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install
```

### 5️⃣ Criar o Banco de Dados

```bash
# Na pasta backend
cd backend
node setup_db.js
```

**O que faz:**
- Cria o banco `infinity_quiz`
- Cria as tabelas vazias

### 6️⃣ Importar os Dados

```bash
# Ainda na pasta backend
node import_db.js
```

**Interação:**
```
📥 Importação do Banco de Dados

🔍 Procurando arquivos .sql na pasta backend...

📂 Arquivos de backup encontrados:

   1. infinity_quiz_backup_2026-02-02.sql (156.42 KB)

Digite o número do arquivo para importar (ou Enter para usar o mais recente): [Enter]

📄 Usando arquivo mais recente: infinity_quiz_backup_2026-02-02.sql

⚠️  ATENÇÃO: Isso irá SUBSTITUIR todos os dados atuais! Continuar? (s/N): s

🔄 Importando banco de dados...

✅ Banco de dados importado com sucesso!
```

### 7️⃣ Iniciar o Projeto

**Terminal 1 - Backend:**
```bash
cd backend
node server.js
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

### 8️⃣ Acessar a Aplicação

- **URL:** http://localhost:5173
- **Login Admin:**
  - Email: `admin123@gmail.com`
  - Senha: `admin123`

---

## 🔧 Troubleshooting (Problemas Comuns)

### ❌ Erro: "mysqldump não encontrado" (ao exportar)

**Causa:** MySQL não está no PATH do Windows

**Solução:**

1. Abrir Painel de Controle
2. Sistema → Configurações avançadas do sistema
3. Variáveis de Ambiente
4. Em "Variáveis do sistema", editar `Path`
5. Adicionar: `C:\Program Files\MySQL\MySQL Server 8.0\bin`
6. Reiniciar terminal

### ❌ Erro: "Access denied" (ao importar)

**Causa:** Senha incorreta no `.env`

**Solução:**

1. Verificar senha do MySQL
2. Atualizar `backend/.env`:
   ```env
   DB_PASS="senha_correta"
   ```

### ❌ Erro: "Unknown database 'infinity_quiz'"

**Causa:** Banco não foi criado

**Solução:**

```bash
cd backend
node setup_db.js
```

### ❌ Erro: "Cannot find module 'dotenv'"

**Causa:** Dependências não instaladas

**Solução:**

```bash
cd backend
npm install
```

### ❌ Frontend não carrega

**Causa:** Backend não está rodando

**Solução:**

1. Verificar se backend está rodando na porta 3000
2. Abrir http://localhost:3000 - deve mostrar erro, mas confirma que está rodando
3. Iniciar frontend: `npm run dev`

---

## 📝 Checklist de Envio

Antes de enviar para seu colega, confirme:

- [ ] Executou `node export_db.js` com sucesso
- [ ] Arquivo `.sql` foi gerado em `backend/`
- [ ] Compactou a pasta `TCC_Infinity` completa
- [ ] Arquivo `.sql` está dentro do ZIP
- [ ] Enviou este guia (`COMPARTILHAR_PROJETO.md`) junto

---

## 📝 Checklist de Recebimento

Seu colega deve verificar:

- [ ] Node.js instalado (`node --version`)
- [ ] MySQL instalado (`mysql --version`)
- [ ] Projeto extraído
- [ ] Arquivo `.env` configurado com senha correta
- [ ] Dependências instaladas (`npm install` em backend e frontend)
- [ ] Banco criado (`node setup_db.js`)
- [ ] Dados importados (`node import_db.js`)
- [ ] Backend rodando (`node server.js`)
- [ ] Frontend rodando (`npm run dev`)
- [ ] Consegue acessar http://localhost:5173

---

## 🆘 Suporte

Se seu colega tiver problemas:

1. **Verificar logs de erro** - Anotar mensagem exata
2. **Consultar** `docs/DATABASE_SETUP.md` - Guia completo de instalação
3. **Verificar versões:**
   ```bash
   node --version   # Deve ser v18+
   mysql --version  # Deve ser 8.0+
   ```

---

## 🎯 Resumo Rápido

### Para VOCÊ (enviando):
```bash
cd backend
node export_db.js
# Compactar pasta TCC_Infinity
# Enviar ZIP para colega
```

### Para SEU COLEGA (recebendo):
```bash
# 1. Instalar Node.js e MySQL
# 2. Extrair projeto
# 3. Configurar backend/.env
# 4. Instalar dependências
cd backend && npm install
cd ../frontend && npm install

# 5. Criar e importar banco
cd ../backend
node setup_db.js
node import_db.js

# 6. Rodar projeto
# Terminal 1: node server.js
# Terminal 2: cd ../frontend && npm run dev
```

---

**✅ Pronto! Seu colega agora tem o projeto completo rodando com todos os dados!**
