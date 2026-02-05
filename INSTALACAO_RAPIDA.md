# TCC Infinity - Instalação Rápida

## Pré-requisitos
1. Node.js: https://nodejs.org/
2. MySQL: https://dev.mysql.com/downloads/installer/

## Instalação

### 1. Instalar dependências
```bash
cd backend
npm install

cd ../frontend
npm install
```

### 2. Configurar MySQL
Edite `backend/.env` com sua senha do MySQL:
```env
DB_PASS="SUA_SENHA_AQUI"
```

### 3. Criar banco de dados
```bash
cd backend
node setup_db.js
node create_admin.js
```

### 4. Executar projeto

**Terminal 1:**
```bash
cd backend
node server.js
```

**Terminal 2:**
```bash
cd frontend
npm run dev
```

### 5. Acessar
http://localhost:5173

## Login Admin
- Email: admin123@gmail.com
- Senha: admin123

## Problemas?

**MySQL não conecta:**
```bash
net start MySQL80
```

**Banco não existe:**
```bash
cd backend
node setup_db.js
```

**Porta em uso:**
Edite `backend/.env` e mude PORT=3001
