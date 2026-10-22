# MW Aprende

Plataforma educacional responsiva para alunos de todas as idades. Inclui uma interface inicial, catálogo de áreas de estudo, exercício demonstrativo, fluxo de cadastro/login Supabase e rota de servidor para professor IA Gemini.

## O que já está neste projeto

- Página inicial responsiva e identidade visual MW Aprende.
- Áreas de Português, Matemática, Ciências/Biologia, História, Geografia, Física/Química, idiomas, Filosofia/Sociologia, computação e educação financeira.
- Trilha de computação com aulas de computador básico, arquivos, internet segura, editor de textos, Excel, programação e inteligência artificial.
- Design atualizado com hero moderno, cartões refinados, seção dedicada à computação e melhor adaptação a telas pequenas.
- Exemplo de exercício com correção e explicação.
- Interface de cadastro e login usando Supabase Auth quando configurado.
- Rota protegida no servidor `/api/tutor` para chamar a Gemini API sem expor a chave no navegador.
- SQL inicial com perfis, progresso e tentativas de quiz, com Row Level Security.

## Importante: estágio do projeto

Este é um **projeto inicial funcional para desenvolvimento**, não uma plataforma de produção já auditada. O progresso mostrado na página é temporário na interface e ainda precisa ser conectado às tabelas para persistência. O catálogo é uma amostra; aulas completas, painel administrativo, recuperação de senha, limitação de uso da IA, moderação e testes de segurança precisam ser implementados/testados antes de abrir ao público. Para crianças, implemente controles de privacidade e consentimento adequados antes do lançamento.

## Requisitos

- Node.js 20+
- Conta Supabase
- Chave da Gemini API (opcional para testar o restante; necessária para o professor IA real)

## Rodar localmente

1. Instale Node.js: https://nodejs.org/
2. Extraia o ZIP e abra a pasta `mw-aprende` no terminal.
3. Rode `npm install`.
4. Copie `.env.example` para `.env.local`.
5. Preencha as chaves do Supabase e, para IA, `GEMINI_API_KEY`.
6. Rode `npm run dev` e abra `http://localhost:3000`.

## Configurar Supabase

1. Crie um projeto em https://supabase.com/.
2. Em Project Settings / API, copie Project URL e anon/public key para `.env.local`.
3. No SQL Editor, execute o conteúdo de `supabase/schema.sql`.
4. Em Authentication, configure os métodos de login e URLs autorizadas. Em desenvolvimento, use `http://localhost:3000`; ao publicar, acrescente a URL de produção.
5. Nunca coloque a `service_role` key no navegador. Este projeto só usa a chave pública no cliente.

## Configurar Professor IA

1. Crie uma chave em https://aistudio.google.com/apikey.
2. Salve como `GEMINI_API_KEY` em `.env.local`.
3. Não use prefixo `NEXT_PUBLIC_` para a chave da IA.
4. Reinicie o servidor. Em hospedagem, adicione a variável no painel do projeto.

A disponibilidade gratuita da API tem limites e condições que podem mudar. Configure limites de uso e monitoramento; a IA não deve ser prometida como ilimitada.

## Publicar

1. Envie a pasta para um repositório GitHub.
2. Importe o repositório no https://vercel.com/.
3. Adicione as variáveis `NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_ANON_KEY` e `GEMINI_API_KEY` em Project Settings → Environment Variables.
4. Faça o deploy e cadastre a URL final nas URLs permitidas do Supabase Auth.
5. Teste cadastro, confirmação de e-mail, login, acesso mobile e o professor IA.

## Serviços externos e custos

- **Supabase:** autenticação e banco de dados. Tem plano gratuito com limites; projetos gratuitos podem ser pausados por inatividade. Confira os limites atuais.
- **Gemini API:** professor de IA. Pode ter faixa gratuita limitada e cobrança por uso conforme modelo/limites; monitore o consumo e nunca exponha a chave.
- **Vercel:** hospedagem e deploy. O plano Hobby tem restrições de uso, inclusive para finalidade comercial. Confira os termos atuais antes de usar publicamente.
- **Domínio próprio:** opcional e normalmente pago.

A plataforma pode ser gratuita para os estudantes, mas isso não garante que os serviços externos permaneçam gratuitos para o responsável pelo projeto.
