# Guia de Deploy na Vercel

## 📋 Pré-requisitos

1. Conta no GitHub (com o código commitado e enviado)
2. Conta na Vercel (gratuita)
3. Projeto configurado corretamente

## 🚀 Método 1: Deploy via Dashboard Vercel (Recomendado)

### Passo 1: Preparar o Repositório
1. Certifique-se de que todo o código está commitado:
   ```bash
   git add .
   git commit -m "Preparando para deploy"
   git push origin main
   ```

### Passo 2: Conectar com Vercel
1. Acesse [vercel.com](https://vercel.com)
2. Faça login com sua conta GitHub
3. Clique em **"Add New Project"** ou **"New Project"**

### Passo 3: Importar o Repositório
1. Selecione o repositório `Estoque_CHS_2026` (ou o nome do seu repositório)
2. O Vercel detectará automaticamente:
   - **Framework Preset**: Vite
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
   - **Install Command**: `npm install`

### Passo 4: Configurar Variáveis de Ambiente (se necessário)
Se você usar variáveis de ambiente no futuro, adicione-as em:
- **Settings** → **Environment Variables**

### Passo 5: Deploy
1. Clique em **"Deploy"**
2. Aguarde o build completar (geralmente 2-5 minutos)
3. Seu site estará disponível em uma URL como: `https://estoque-chs-2026.vercel.app`

## 🖥️ Método 2: Deploy via CLI

### Passo 1: Instalar Vercel CLI
```bash
npm install -g vercel
```

### Passo 2: Fazer Login
```bash
vercel login
```
Isso abrirá o navegador para autenticação.

### Passo 3: Deploy
```bash
vercel
```

Siga as instruções:
- **Set up and deploy?** → `Y`
- **Which scope?** → Selecione sua conta
- **Link to existing project?** → `N` (primeira vez) ou `Y` (se já existe)
- **What's your project's name?** → `estoque-chs-2026` (ou o nome desejado)
- **In which directory is your code located?** → `./` (pressione Enter)

### Passo 4: Deploy de Produção
Após o primeiro deploy, para fazer deploy em produção:
```bash
vercel --prod
```

## ⚙️ Configurações Aplicadas

O projeto já está configurado com:

### `vercel.json`
- Build Command: `npm run build`
- Output Directory: `dist`
- Rewrites configurados para SPA (Single Page Application)

### `vite.config.ts`
- Base path: `/`
- Output directory: `dist`
- Build otimizado para produção

## 🔍 Verificando o Deploy

Após o deploy, verifique:
1. ✅ O build foi concluído com sucesso
2. ✅ O site está acessível na URL fornecida
3. ✅ Todas as rotas funcionam corretamente
4. ✅ A conexão com Supabase está funcionando

## 🐛 Solução de Problemas

### Erro: "Failed to resolve import"
- ✅ Já corrigido na configuração do Vite

### Erro: "Build failed"
- Verifique os logs de build no dashboard da Vercel
- Certifique-se de que todas as dependências estão no `package.json`

### Erro: "Module not found"
- Execute `npm install` localmente para verificar dependências
- Verifique se o `node_modules` está no `.gitignore`

### Site não carrega
- Verifique se o `vercel.json` está configurado corretamente
- Confirme que o `outputDirectory` está como `dist`

## 📝 Notas Importantes

1. **Supabase**: As credenciais estão configuradas no código. Se precisar mudar, edite `src/integrations/supabase/client.ts`

2. **Build Local**: Teste o build localmente antes de fazer deploy:
   ```bash
   npm run build
   npm run preview
   ```

3. **Atualizações**: Após cada push para a branch `main`, o Vercel fará deploy automático (se configurado)

4. **Domínio Customizado**: Você pode adicionar um domínio customizado nas configurações do projeto na Vercel

## 🎉 Pronto!

Seu projeto estará online e acessível após o deploy bem-sucedido!


