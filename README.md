# 🚀 TCC Infinity - Guia de Instalação Rápida

> **Aplicativo de Quiz Educacional com PWA**

## 📦 O que você recebeu

Este projeto é um aplicativo web de quiz educacional que funciona offline (PWA). Ele possui:
- ✅ Sistema de login e registro
- ✅ Quiz com 100+ perguntas em 3 categorias
- ✅ Sistema de ranking
- ✅ Painel administrativo
- ✅ Funciona offline após instalação

---

## ⚡ Instalação Rápida (5 passos)

### 1️⃣ Instalar Node.js

**Download:** https://nodejs.org/ (versão LTS)

Após instalar, verificar:
```bash
node --version
```

### 2️⃣ Instalar MySQL

**Download:** https://dev.mysql.com/downloads/installer/ (Windows)

Durante a instalação:
- Escolha: **Developer Default**
- Defina senha do root (ex: `Pedro12345#`)
- ⚠️ **ANOTE ESSA SENHA!**

Verificar instalação:
```bash
mysql --version
```

### 3️⃣ Configurar o Projeto

Extraia o ZIP e abra o terminal na pasta do projeto.

**Instalar dependências:**
```bash
cd backend
npm install

cd ../frontend
npm install
```

**Configurar senha do MySQL:**

Edite o arquivo `backend/.env` e coloque sua senha do MySQL:
```env
DB_PASS="SUA_SENHA_AQUI"
```

### 4️⃣ Criar o Banco de Dados

```bash
cd backend
node setup_db.js
node create_admin.js
```

**Credenciais do Admin:**
- Email: `admin123@gmail.com`
- Senha: `admin123`

### 5️⃣ Iniciar o Projeto

**Abra 2 terminais:**

**Terminal 1 (Backend):**
```bash
cd backend
node server.js
```

**Terminal 2 (Frontend):**
```bash
cd frontend
npm run dev
```

**Acessar:** http://localhost:5173

---

## 🎮 Como Usar

### Usuário Normal:
1. Registre-se em `/register`
2. Faça login
3. Escolha uma categoria
4. Responda 10 perguntas
5. Veja sua pontuação e ranking

### Administrador:
1. Login com: `admin123@gmail.com` / `admin123`
2. Acesse `/admin`
3. Gerencie perguntas (adicionar, editar, deletar)

### Instalar como App:
1. Clique no banner "Instalar App" que aparece
2. Ou use o ícone de instalação no navegador
3. O app funcionará offline!

---

## 📁 Estrutura do Projeto

```
TCC_Infinity/
├── backend/              # Servidor Node.js + MySQL
│   ├── .env             # ⚠️ Configurar senha aqui
│   ├── server.js        # Iniciar servidor
│   ├── setup_db.js      # Criar banco
│   ├── create_admin.js  # Criar admin
│   └── schema.sql       # Estrutura do banco
├── frontend/            # Interface React + Vite
│   ├── src/            # Código fonte
│   └── public/         # Arquivos estáticos + PWA
└── docs/               # Documentação técnica
```

---

## 🗄️ Banco de Dados

### Tabelas:
- **users** - Usuários e admins
- **categorias** - Categorias de quiz (Tecnologia, Ciências, História)
- **questions** - 100+ perguntas
- **scores** - Pontuações dos usuários

### Comandos Úteis:

**Acessar MySQL:**
```bash
mysql -u root -p
```

**Ver dados:**
```sql
USE infinity_quiz;
SHOW TABLES;
SELECT COUNT(*) FROM questions;
SELECT * FROM users;
```

**Resetar pontuações:**
```sql
DELETE FROM scores;
```

---

## 🔧 Problemas Comuns

### ❌ Erro: "Cannot connect to MySQL"
**Solução:** Verificar se MySQL está rodando
```bash
# Windows
net start MySQL80
```

### ❌ Erro: "Access denied"
**Solução:** Senha incorreta no `.env`
- Edite `backend/.env`
- Coloque a senha correta do MySQL

### ❌ Erro: "Database doesn't exist"
**Solução:** Execute o setup
```bash
cd backend
node setup_db.js
```

### ❌ Erro: "Port 3000 already in use"
**Solução:** Feche outros programas usando a porta ou mude no `.env`:
```env
PORT=3001
```

### ❌ Frontend não carrega
**Solução:** Certifique-se que ambos servidores estão rodando
- Backend: `node server.js` (porta 3000)
- Frontend: `npm run dev` (porta 5173)

---

## 📋 Checklist Rápido

- [ ] Node.js instalado
- [ ] MySQL instalado e rodando
- [ ] Senha do MySQL configurada no `.env`
- [ ] `npm install` executado no backend
- [ ] `npm install` executado no frontend
- [ ] `node setup_db.js` executado
- [ ] `node create_admin.js` executado
- [ ] Backend rodando (porta 3000)
- [ ] Frontend rodando (porta 5173)
- [ ] Site abre em http://localhost:5173

---

## 🎯 Comandos Resumidos

```bash
# Setup inicial (executar uma vez)
cd backend
npm install
node setup_db.js
node create_admin.js

cd ../frontend
npm install

# Executar diariamente
# Terminal 1
cd backend
node server.js

# Terminal 2
cd frontend
npm run dev
```

---

## 📱 PWA (Progressive Web App)

O projeto pode ser instalado como aplicativo:

1. Abra no Chrome/Edge
2. Clique em "Instalar App" no banner
3. O app aparecerá na área de trabalho
4. Funciona offline após instalação!

**Ícones PWA:** Já estão em `frontend/public/icons/`

---

## 🔐 Segurança

**Padrão:**
- Admin: `admin123@gmail.com` / `admin123`

**Para produção:**
- Mude a senha do admin
- Use HTTPS
- Configure variáveis de ambiente seguras

---

## 📚 Documentação Completa

Para mais detalhes técnicos, consulte:
- `docs/DATABASE_SETUP.md` - Banco de dados detalhado
- `docs/PWA_DOCUMENTATION.md` - Implementação PWA

---

## ✅ Pronto!

Se tudo funcionou:
- ✅ Site abre em http://localhost:5173
- ✅ Consegue fazer login
- ✅ Quiz funciona
- ✅ Ranking aparece
- ✅ Admin consegue gerenciar perguntas

**Qualquer problema, consulte a seção "Problemas Comuns" acima.**

---

**Desenvolvido para TCC Infinity** 🚀  
*Versão: 1.0 | Janeiro 2026*
