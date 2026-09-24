# Trabalho de Graduação

Aplicativo móvel voltado ao apoio de adultos insuficientemente ativos na organização da prática de atividades físicas.

O projeto está sendo desenvolvido como Trabalho de Graduação e reúne planejamento de rotina, treinos, registro de atividades, gamificação e recursos de comunidade. O nome definitivo do aplicativo ainda será definido.

## Situação do projeto

O projeto encontra-se em desenvolvimento. A estrutura inicial já possui:

- aplicativo mobile criado com React Native, Expo e TypeScript;
- API criada com NestJS e TypeScript;
- PostgreSQL executado em contêiner Docker;
- organização inicial das variáveis de ambiente;
- documentação e modelagem em desenvolvimento.

## Tecnologias

### Aplicativo mobile

- React Native
- Expo
- TypeScript
- Expo Router

### Back-end

- Node.js
- NestJS
- TypeScript
- Prisma ORM, previsto para a integração com o banco de dados

### Banco de dados e infraestrutura

- PostgreSQL
- Docker
- Docker Compose

## Estrutura do repositório

```text
TrabalhoDeGraduacao/
├── backend/              # API desenvolvida com NestJS
├── mobile/               # Aplicativo desenvolvido com React Native e Expo
├── docker-compose.yaml   # Configuração do PostgreSQL no Docker
├── .env.example          # Modelo das variáveis de ambiente
├── .gitignore
└── README.md
```

## Pré-requisitos

Antes de iniciar, instale:

- Node.js 24 LTS;
- npm;
- Docker Desktop;
- Git.

Para testar no celular, instale também o aplicativo Expo Go.

## Configuração inicial

### 1. Clonar o repositório

```bash
git clone URL_DO_REPOSITORIO
cd TrabalhoDeGraduacao
```

Substitua `URL_DO_REPOSITORIO` pelo endereço do projeto no GitHub.

### 2. Criar o arquivo de ambiente

No Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

No Linux ou macOS:

```bash
cp .env.example .env
```

Depois, ajuste a senha no arquivo `.env`.

Exemplo:

```env
POSTGRES_DB=tg_app
POSTGRES_USER=tg_user
POSTGRES_PASSWORD=troque_esta_senha
POSTGRES_PORT=5433

DATABASE_URL=postgresql://tg_user:troque_esta_senha@localhost:5433/tg_app?schema=public
```

O arquivo `.env` contém informações locais e não deve ser enviado ao GitHub.

## Banco de dados

Inicie o PostgreSQL:

```bash
docker compose up -d
```

Verifique o contêiner:

```bash
docker compose ps
```

Visualize os logs do serviço PostgreSQL:

```bash
docker compose logs -f postgres
```

Para interromper a visualização dos logs, pressione `Ctrl + C`.

O banco do Docker fica disponível em:

```text
localhost:5433
```

Para encerrar os contêineres sem apagar os dados:

```bash
docker compose down
```

O comando `docker compose down -v` também remove o volume e apaga os dados do banco. Ele deve ser utilizado somente quando houver intenção de recriar o banco do zero.

## Back-end

Entre na pasta da API e instale as dependências:

```bash
cd backend
npm ci
```

Execute em modo de desenvolvimento:

```bash
npm run start:dev
```

A API fica disponível em:

```text
http://localhost:3000
```

Para executar os testes:

```bash
npm test
```

## Aplicativo mobile

Em outro terminal, entre na pasta do aplicativo e instale as dependências:

```bash
cd mobile
npm ci
```

Inicie o Expo:

```bash
npm start
```

No terminal do Expo:

- pressione `w` para abrir no navegador;
- pressione `a` para abrir no Android;
- escaneie o QR Code com o Expo Go para abrir no celular;
- pressione `r` para recarregar o aplicativo;
- pressione `Ctrl + C` para encerrar.

Para executar diretamente no navegador:

```bash
npm run web
```

Para verificar o código:

```bash
npm run lint
```

## Portas utilizadas

| Serviço | Porta | Endereço |
|---|---:|---|
| NestJS | 3000 | `http://localhost:3000` |
| Expo Web | 8081 | `http://localhost:8081` |
| PostgreSQL instalado localmente | 5432 | `localhost:5432` |
| PostgreSQL no Docker | 5433 | `localhost:5433` |

## Desenvolvimento em equipe

Cada integrante terá seu próprio arquivo `.env`, banco local e volume Docker. O repositório deve compartilhar:

- código-fonte;
- arquivos `package.json`;
- arquivos `package-lock.json`;
- `.env.example`;
- migrações do Prisma;
- documentação do projeto.

Não devem ser enviados:

- `.env`;
- `node_modules`;
- dados locais do banco;
- senhas ou chaves de acesso.

Ao baixar alterações que modificam dependências, execute `npm ci` na pasta correspondente.

## Escopo acadêmico

No TG 1, o foco está na documentação, no levantamento de requisitos, na modelagem, na prototipagem e na implementação inicial do acesso ao sistema.

No TG 2, serão desenvolvidas as demais funcionalidades planejadas e realizados testes de usabilidade.

## Observação

Este projeto possui finalidade acadêmica e está em fase inicial de desenvolvimento. Funcionalidades e decisões técnicas poderão ser ajustadas durante as orientações e avaliações do TG.
