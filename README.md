# NLW Agents - Sistema de Perguntas com IA

## 📝 Descrição

O **NLW Agents** é uma aplicação inovadora desenvolvida durante o **NLW 20 (Next Level Week) da RocketSeat - Trilha Intermediária**. O projeto combina inteligência artificial com processamento de áudio para criar uma experiência interativa de perguntas e respostas.

O sistema permite que usuários criem salas de estudo/trabalho, gravem áudios explicativos sobre qualquer tópico e façam perguntas que são respondidas automaticamente pela IA do Google Gemini com base no conteúdo dos áudios gravados. Utiliza busca semântica com vetores (embeddings) para encontrar o contexto mais relevante nos áudios transcritos.

### 🎯 Objetivo do Projeto

Este projeto foi desenvolvido como parte do evento **NLW 20 da RocketSeat** e demonstra a implementação de conceitos avançados como:

- Integração com IA Generativa (Google Gemini)
- Processamento e transcrição de áudio
- Busca semântica com vetores (pgvector)
- Arquitetura fullstack moderna com TypeScript

## 🏗️ Arquitetura do Projeto

### Backend (Server)

- **Framework**: Fastify com TypeScript
- **Banco de Dados**: PostgreSQL com extensão pgvector
- **ORM**: Drizzle ORM
- **IA**: Google Gemini API
- **Processamento**: Transcrição de áudio e geração de embeddings

### Frontend (Web)

- **Framework**: React 18+ com TypeScript
- **Roteamento**: React Router DOM
- **Gerenciamento de Estado**: TanStack Query (React Query)
- **Estilização**: Tailwind CSS
- **Componentes**: Radix UI
- **Build Tool**: Vite

## 🚀 Funcionalidades

### 1. Gerenciamento de Salas

- ✅ Criação de salas com nome e descrição
- ✅ Listagem de todas as salas criadas
- ✅ Contador de perguntas por sala

### 2. Gravação e Processamento de Áudio

- ✅ Gravação de áudio em tempo real
- ✅ Transcrição automática usando Gemini AI
- ✅ Geração de embeddings para busca semântica
- ✅ Armazenamento de chunks de áudio com vetores

### 3. Sistema de Perguntas Inteligente

- ✅ Criação de perguntas textuais
- ✅ Busca semântica nos áudios gravados
- ✅ Geração de respostas contextualizadas pela IA
- ✅ Histórico de perguntas e respostas por sala

## 🛠️ Tecnologias Utilizadas

### Backend (Node.js TypeScript Nativo)

```json
{
  "runtime": "Node.js 18+ com TypeScript nativo (--experimental-strip-types)",
  "framework": "Fastify 5.4.0",
  "database": "PostgreSQL com pgvector (pg17)",
  "orm": "Drizzle ORM 0.44.2",
  "ai": "Google Gemini API (@google/genai 1.9.0)",
  "validation": "Zod 3.25.75",
  "cors": "@fastify/cors 11.0.1",
  "multipart": "@fastify/multipart 9.0.3",
  "migrations": "Drizzle Kit 0.31.4"
}
```

### Frontend (React 19 + Vite)

```json
{
  "framework": "React 19.1.0",
  "language": "TypeScript 5.8.3",
  "build": "Vite 7.0.3",
  "styling": "Tailwind CSS 4.1.11",
  "components": "Radix UI + shadcn/ui",
  "forms": "React Hook Form 7.60.0 + Zod 4.0.0",
  "http": "TanStack Query 5.81.5",
  "routing": "React Router DOM 7.6.3",
  "icons": "Lucide React 0.525.0",
  "date": "Day.js 1.11.13"
}
```

## 📁 Estrutura do Projeto

```bash
nlw-agents/
├── server/                          # Backend da aplicação
│   ├── src/
│   │   ├── db/                      # Configuração do banco de dados
│   │   │   ├── schema/              # Esquemas das tabelas
│   │   │   │   ├── rooms.ts         # Tabela de salas
│   │   │   │   ├── questions.ts     # Tabela de perguntas
│   │   │   │   ├── audio-chunks.ts  # Tabela de chunks de áudio
│   │   │   │   └── index.ts         # Exportação dos schemas
│   │   │   ├── connection.ts        # Conexão com o banco
│   │   │   ├── seed.ts              # Dados iniciais
│   │   │   └── migrations/          # Migrações do banco
│   │   ├── http/
│   │   │   └── routes/              # Rotas da API
│   │   │       ├── create-room.ts          # POST /rooms
│   │   │       ├── get-rooms.ts            # GET /rooms
│   │   │       ├── create-question.ts      # POST /rooms/:id/questions
│   │   │       ├── get-room-questions.ts   # GET /rooms/:id/questions
│   │   │       └── upload-audio.ts         # POST /rooms/:id/audio
│   │   ├── services/
│   │   │   └── gemini.ts            # Integração com Gemini AI
│   │   ├── env.ts                   # Configuração de variáveis de ambiente
│   │   └── server.ts                # Configuração do servidor
│   ├── docker/
│   │   └── setup.sql                # Script de inicialização do DB
│   ├── docker-compose.yml           # Configuração do PostgreSQL
│   └── package.json
│
└── web/                             # Frontend da aplicação
    ├── src/
    │   ├── components/              # Componentes React
    │   │   ├── ui/                  # Componentes base (shadcn/ui)
    │   │   ├── create-room-form.tsx # Formulário de criação de sala
    │   │   ├── room-list.tsx        # Lista de salas
    │   │   ├── question-form.tsx    # Formulário de perguntas
    │   │   ├── question-item.tsx    # Item de pergunta/resposta
    │   │   └── question-list.tsx    # Lista de perguntas
    │   ├── pages/                   # Páginas da aplicação
    │   │   ├── create-room.tsx      # Página inicial
    │   │   ├── room.tsx             # Página da sala
    │   │   └── record-room-audio.tsx # Página de gravação
    │   ├── http/                    # Hooks de requisições HTTP
    │   │   ├── use-create-room.ts
    │   │   ├── use-rooms.ts
    │   │   ├── use-create-question.ts
    │   │   ├── use-room-questions.ts
    │   │   └── types/               # Tipos TypeScript das APIs
    │   ├── lib/                     # Utilitários
    │   ├── app.tsx                  # Configuração principal
    │   └── main.tsx                 # Ponto de entrada
    └── package.json
```

## 🗄️ Esquema do Banco de Dados

### Tabela: `rooms`

```sql
- id (UUID, PK)
- name (TEXT, NOT NULL)
- description (TEXT)
- created_at (TIMESTAMP, DEFAULT NOW())
```

### Tabela: `questions`

```sql
- id (UUID, PK)
- room_id (UUID, FK -> rooms.id)
- question (TEXT, NOT NULL)
- answer (TEXT)
- created_at (TIMESTAMP, DEFAULT NOW())
```

### Tabela: `audio_chunks`

```sql
- id (UUID, PK)
- room_id (UUID, FK -> rooms.id)
- transcription (TEXT, NOT NULL)
- embeddings (VECTOR(768), NOT NULL)
- created_at (TIMESTAMP, DEFAULT NOW())
```

## 🔧 Configuração e Instalação

### Pré-requisitos

- Node.js 18+
- Docker e Docker Compose
- Conta no Google AI Studio (para API do Gemini)

### 1. Clonagem do Repositório

```bash
git clone https://github.com/johncobain/nlw-agents.git
cd nlw-agents
```

### 2. Configuração do Backend

#### 2.1 Instalação das Dependências

```bash
cd server
npm install
```

#### 2.2 Configuração das Variáveis de Ambiente

Crie um arquivo `.env` na pasta `server`:

```env
PORT=3333
DATABASE_URL=postgresql://docker:docker@localhost:5431/agents
GEMINI_API_KEY=sua_chave_do_gemini_aqui
```

#### 2.3 Inicialização do Banco de Dados

```bash
# Subir o PostgreSQL com pgvector
docker-compose up -d

# Executar migrações
npm run db:migrate

# (Opcional) Popular com dados iniciais
npm run db:seed
```

#### 2.4 Execução do Servidor

```bash
# Desenvolvimento
npm run dev

# Produção
npm start
```

### 3. Configuração do Frontend

#### 3.1 Instalação das Dependências

```bash
cd web
npm install
```

#### 3.2 Execução do Frontend

```bash
# Desenvolvimento
npm run dev

# Build para produção
npm run build
```

## 🔄 Fluxo de Funcionamento Detalhado

### 1. Criação de Sala

1. Usuário acessa a página inicial (`/`)
2. Preenche o formulário com nome e descrição da sala (validação com Zod)
3. Request POST para `/rooms` com os dados validados
4. Drizzle ORM insere nova sala no PostgreSQL
5. TanStack Query invalida cache e atualiza lista
6. Usuário é redirecionado para `/room/:id`

### 2. Gravação e Processamento de Áudio (Técnico)

1. Na sala, usuário clica em "Gravar Áudio" → navega para `/room/:id/audio`
2. Sistema solicita permissão do microfone via `navigator.mediaDevices.getUserMedia`
3. `MediaRecorder` inicia gravação em formato WebM (64kbps)
4. **Chunks de 10 segundos**: A cada 10s, o sistema automaticamente:
   - Para a gravação atual
   - Envia o chunk via FormData para `POST /rooms/:id/audio`
   - Reinicia nova gravação
5. **Backend processa cada chunk**:
   - Converte áudio para Base64
   - Envia para Gemini API com prompt específico para transcrição em PT-BR
   - Gera embeddings (768 dimensões) usando modelo `text-embedding-004`
   - Armazena no PostgreSQL: `audio_chunks(transcription, embeddings, room_id)`

### 3. Sistema de Perguntas com IA (Algoritmo Detalhado)

1. **Input da pergunta**: Usuário digita pergunta na sala
2. **Geração de embeddings**: Sistema gera embeddings da pergunta usando Gemini
3. **Busca semântica**:

   ```sql
   -- Busca por similaridade coseno com threshold de 70%
   SELECT transcription, (1 - (embeddings <=> question_embeddings)) as similarity
   FROM audio_chunks
   WHERE room_id = ?
   AND (1 - (embeddings <=> question_embeddings)) > 0.7
   ORDER BY embeddings <=> question_embeddings
   LIMIT 5
   ```

4. **Geração da resposta**: Se encontrou chunks relevantes:
   - Concatena transcrições dos 5 chunks mais similares
   - Envia para Gemini com prompt estruturado incluindo contexto
   - IA gera resposta baseada apenas no contexto fornecido
5. **Persistência**: Salva pergunta e resposta no banco
6. **Real-time**: TanStack Query atualiza interface automaticamente

### 4. Arquitetura de Busca Semântica

- **Vetores**: Embeddings de 768 dimensões (text-embedding-004)
- **Distância**: Similaridade coseno com operator `<=>` do pgvector
- **Threshold**: 70% de similaridade mínima
- **Limite**: Máximo 5 chunks mais relevantes por pergunta
- **Performance**: Índice automático em vetores para busca otimizada

## 🔍 APIs Disponíveis

### Salas

```http
GET    /rooms                    # Lista todas as salas
POST   /rooms                    # Cria nova sala
GET    /rooms/:id/questions      # Lista perguntas da sala
POST   /rooms/:id/questions      # Cria pergunta na sala
POST   /rooms/:id/audio          # Upload de áudio para a sala
```

### Health Check

```http
GET    /health                   # Verifica status do servidor
```

## 🎯 Casos de Uso

### Educação

- Gravação de aulas
- Perguntas sobre conteúdo específico
- Revisão de tópicos

### Reuniões Corporativas

- Gravação de meetings
- FAQ automático
- Consulta de decisões

### Podcasts/Entrevistas

- Transcrição automática
- Sistema de perguntas para ouvintes
- Busca por temas específicos

## 🔒 Segurança e Limitações

### Segurança

- Validação de dados com Zod
- CORS configurado
- Sanitização de uploads

### Limitações Atuais

- Áudios limitados a formato WebM
- Sem autenticação de usuários
- Sem limite de salas por usuário
- Dependência da API do Gemini

## 📊 Métricas e Performance

### Backend

- Chunks de áudio processados em até 10 segundos
- Busca semântica otimizada com pgvector
- Cache de embeddings para eficiência

### Frontend

- Interface responsiva
- Carregamento otimizado com React Query
- Componentes reutilizáveis

## 🧪 Testes

### Como Testar

1. Criar uma sala
2. Gravar alguns áudios explicativos
3. Fazer perguntas relacionadas ao conteúdo
4. Verificar a qualidade das respostas

### Cenários de Teste

- Perguntas diretas sobre o conteúdo
- Perguntas fora do contexto
- Múltiplos áudios na mesma sala
- Diferentes tipos de conteúdo

## 🤝 Contribuição

Para contribuir com o projeto:

1. Fork o repositório
2. Crie uma branch para sua feature
3. Implemente as mudanças
4. Adicione testes se necessário
5. Submeta um Pull Request

## 📝 Licença

Este projeto é open source e está disponível sob a licença MIT.

## 🙋‍♂️ Suporte

Para dúvidas ou problemas:

- Abra uma issue no repositório
- Consulte a documentação das APIs utilizadas
- Verifique os logs do servidor para debugging

## 🚀 Diferenciais Técnicos

### Inovações Implementadas

- **TypeScript Nativo**: Uso do flag `--experimental-strip-types` do Node.js, eliminando transpilação
- **Busca Semântica Avançada**: Implementação de similaridade coseno com pgvector
- **Streaming de Áudio**: Processamento em tempo real com chunks de 10s
- **IA Contextual**: Respostas baseadas apenas no conteúdo dos áudios gravados
- **Interface Responsiva**: Design moderno com Tailwind CSS 4 e Radix UI
- **Arquitetura Moderna**: Stack completamente atualizada (React 19, Fastify 5, etc.)

### Performance e Escalabilidade

- **Embeddings Cachados**: Vetores armazenados para busca otimizada
- **Queries Otimizadas**: Uso eficiente de índices vetoriais
- **Real-time Updates**: TanStack Query para sincronização automática
- **Processamento Assíncrono**: Áudio processado em background

---

**Desenvolvido como parte do NLW 20 (Next Level Week) da RocketSeat - Trilha Intermediária**  
_Um projeto que demonstra a integração entre IA Generativa, processamento de áudio, busca semântica e desenvolvimento web fullstack moderno com TypeScript._

### 🏆 Tecnologias de Ponta Utilizadas

- Google Gemini 2.5 Flash para IA
- PostgreSQL com extensão pgvector
- React 19 com Concurrent Features
- TypeScript nativo no Node.js
- Fastify para alta performance
