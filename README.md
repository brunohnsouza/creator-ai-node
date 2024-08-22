# creator.ai

Aplicação que possibilita realizar upload de videos e por meio de IA, criar automaticamente títulos chamativos e descrições com um boa indexação.

## Índice

- [Requisitos](#requisitos)
- [Instalação](#instalação)
- [Endpoints](#endpoints)
- [Licença](#licença)

## Requisitos

- **Node.js**
- **TypeScript**
- **Prisma**
- **Fastify**
- **Zod**
- **SQLite**
- **OpenAI Node API**

## Instalação

Siga as etapas abaixo para configurar e instalar a API em seu ambiente local:

1. Clone o repositório e acesse o diretório:

```bash
git clone git@github.com:brunohnsouza/creator-ai-node.git
cd creator-ai-node
```

2. Instale as dependências do projeto usando o `Node Package Manager (NPM)`:

```bash
npm install
```

3. Inicie o servidor em modo de desenvolvimento:

```bash
npm run dev
```

A API estará acessível em `http://localhost:3333`.

## Endpoints

Principais endpoints da API, com informações sobre seus métodos HTTP, descrição, parâmetros, exemplos de solicitações e exemplos de respostas.

| Endpoint                        | Método | Descrição                                                                                           | Parâmetros                                                                                                                                                                                 | Exemplo de Solicitação                                                                                                                                 | Exemplo de Resposta                                                              |
| ------------------------------- | ------ | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| /videos/{videoId}/transcription | POST   | Cria a transcrição de um vídeo com base no ID fornecido e no prompt passado no corpo da solicitação | `videoId` (UUID, parâmetro de rota), `prompt` (string, parâmetro no corpo da solicitação)                                                                                                  | POST /videos/123e4567-e89b-12d3-a456-426614174000/transcription Body: `{ "prompt": "Iniciar transcrição para o vídeo" }`                               | `{ "transcription": "Texto..." }`                                                |
| /ai/complete                    | POST   | Gera uma conclusão de IA usando uma transcrição de vídeo existente e um prompt personalizado        | `videoId` (UUID, parâmetro no corpo da solicitação), `prompt` (string, parâmetro no corpo da solicitação), `temperature` (number, parâmetro no corpo da solicitação, opcional, padrão 0.5) | POST /ai/complete Body: `{ "videoId": "123e4567-e89b-12d3-a456-426614174000", "prompt": "Resuma a transcrição: {transcription}", "temperature": 0.7 }` | Fluxo contínuo de texto gerado pela IA                                           |
| /prompts                        | GET    | Retorna uma lista de todos os prompts                                                               | Nenhum                                                                                                                                                                                     | GET /prompts                                                                                                                                           | `[ { "id": "1", "text": "Prompt 1" }, { "id": "2", "text": "Prompt 2" } ]`       |
| /videos                         | POST   | Faz upload de um arquivo de vídeo no formato MP3                                                    | Arquivo de vídeo (MP3)                                                                                                                                                                     | POST /videos Arquivo: `audio mp3`                                                                                                                      | `{ "video": { "id": "1", "name": "audio.mp3", "path": "/tmp/audio-uuid.mp3" } }` |

## Licença

[MIT](https://choosealicense.com/licenses/mit/)
