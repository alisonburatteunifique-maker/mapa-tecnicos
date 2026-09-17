# Projeto 5 — Mapa de Baixa de Sinal

Versão preparada para hospedagem estática no GitHub Pages. Não usa `npm`, Netlify ou processo de build.

## Publicação
1. Crie um repositório no GitHub.
2. Envie o conteúdo desta pasta para a branch `main`.
3. Em **Settings → Pages**, escolha **GitHub Actions**.
4. O workflow em `.github/workflows/deploy.yml` publica o site automaticamente a cada push.

## Supabase
A aplicação continua usando o Supabase para status compartilhados e Realtime. A tabela `public.clientes_status` precisa conter:

```sql
id text primary key,
status text,
obs text,
updated_at timestamptz,
updated_by text
```

Se `updated_by` ainda não existir:

```sql
ALTER TABLE public.clientes_status
ADD COLUMN IF NOT EXISTS updated_by TEXT;
```

## Atenção sobre dados
O GitHub Pages publica arquivos estáticos na internet. Esta versão contém dados de clientes no HTML, e o acesso atual identifica o técnico apenas pelo nome digitado. Antes de publicar em um repositório público, valide as regras de acesso/RLS do Supabase e a política interna de proteção de dados da empresa.
