# Guia de Hospedagem na Vercel - Infinity Quiz

## 📋 Pré-requisitos

1. **Conta na Vercel** - Crie em [vercel.com](https://vercel.com)
2. **Repositório no GitHub** - Faça push do seu projeto
3. **Banco de dados** - Escolha uma opção:
   - **Recomendado**: Vercel Postgres ou PlanetScale (MySQL)
   - Alternativa: Seu próprio servidor MySQL

## 🚀 Passos para Deploy

### 1. Preparar o Repositório

```bash
# Certifique-se que o projeto está no GitHub
git add .
git commit -m "Preparação para Vercel"
git push origin main
```

### 2. Configurar Banco de Dados

**Opção A: Usar Vercel Postgres** (mais simples)
```bash
# Via CLI da Vercel
vercel postgres
```

**Opção B: PlanetScale (MySQL)**
- Crie uma conta em [planetscale.com](https://planetscale.com)
- Crie um banco de dados
- Obtenha as credenciais de conexão

### 3. Importar no Vercel

1. Acesse [vercel.com/dashboard](https://vercel.com/dashboard)
2. Clique em "Add New Project"
3. Selecione seu repositório GitHub
4. Configure:
   - **Framework Preset**: Other
   - **Root Directory**: `.` (raiz do projeto)
   - **Build Command**: 
     ```
     npm --prefix frontend run build
     ```
   - **Install Command**: 
     ```
     npm install && npm --prefix backend install && npm --prefix frontend install
     ```

### 4. Variáveis de Ambiente

No dashboard da Vercel, vá para **Settings > Environment Variables** e adicione:

```
DB_HOST = seu_host
DB_USER = seu_usuario
DB_PASSWORD = sua_senha
DB_NAME = seu_banco
GEMINI_API_KEY = sua_chave_api
JWT_SECRET = sua_chave_secreta_jwt
NODE_ENV = production
```

### 5. Atualizar server.js para Vercel

O arquivo `backend/server.js` já está configurado corretamente! A Vercel exportará automaticamente como Serverless Function.

### 6. Deploy

Simplesmente faça um push para seu repositório:

```bash
git add .
git commit -m "Deploy configs"
git push origin main
```

A Vercel detectará as mudanças e iniciará o build automaticamente.

## ⚙️ Configurações Especiais

### Frontend (Vite)

A build está configurada para gerar em `frontend/dist`. O `vercel.json` serve os arquivos estáticos corretamente.

### Backend (Express)

- Rota de API: `/api/*` → `backend/server.js`
- Rota raiz e SPA: `/*` → `frontend/dist/index.html`

### Proxy de Desenvolvimento

Quando desenvolver localmente, o Vite já está configurado para fazer proxy das APIs para `http://localhost:3000`.

## 🔒 Banco de Dados Recomendado

Para máximo de compatibilidade:

**PlanetScale (MySQL)**
```
DB_HOST: seu_host.psdb.cloud
DB_USER: seu_usuario
DB_PASSWORD: sua_senha_secreta
DB_NAME: seu_banco
```

**Vercel Postgres** (se preferir PostgreSQL)
- Será fornecida uma connection string

## 🧪 Testar Localmente Antes

```bash
# Frontend
cd frontend
npm run build
npm run preview

# Backend (em outro terminal)
cd backend
npm start
```

## 📝 Variáveis de Ambiente Importantes

- `JWT_SECRET`: Gere uma chave segura aleatória
- `GEMINI_API_KEY`: Sua chave da API do Google Generative AI
- `NODE_ENV`: Sempre `production` na Vercel

## 🆘 Troubleshooting

| Problema | Solução |
|----------|---------|
| Erro 404 nas rotas | Verifique se o `vercel.json` está correto |
| Erro de CORS | Configure CORS no `server.js` para a URL da Vercel |
| Conexão BD falha | Verifique credenciais e whitelist de IP |
| Build falha | Veja os logs em Vercel > Deployments |

## 📞 URLs Após Deploy

- **Frontend**: `https://seu-projeto.vercel.app`
- **API**: `https://seu-projeto.vercel.app/api`
- **Banco**: Suas credenciais do PlanetScale/Postgres

---

Após o deploy, atualize a URL da API no frontend se necessário em `frontend/src/services/api.js`.
