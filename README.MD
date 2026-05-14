# API Formula 1

API simples feita em Node.js e TypeScript para consultar dados basicos de equipes e pilotos de Formula 1.

O projeto usa Fastify para criar o servidor HTTP, `@fastify/cors` para liberar acesso de outras aplicacoes e `tsx` para executar o codigo TypeScript em ambiente de desenvolvimento.

## O que a API faz

- Lista equipes de Formula 1.
- Lista pilotos cadastrados.
- Busca um piloto pelo `id`.
- Retorna erro `404` quando o piloto nao existe.

## Tecnologias usadas

- Node.js
- TypeScript
- Fastify
- @fastify/cors
- tsx
- tsup

## Como instalar

No terminal, dentro da pasta do projeto, execute:

```bash
npm install
```

## Como executar em desenvolvimento

```bash
npm run start:dev
```

Por padrao a API roda na porta `3333`, definida no arquivo `.env`:

```env
PORT=3333
```

Depois de iniciar o servidor, acesse:

```text
http://localhost:3333/teams
http://localhost:3333/drivers
http://localhost:3333/drivers/1
```

## Como gerar build

```bash
npm run dist
```

O build e gerado na pasta `dist`.

## Como executar a versao buildada

```bash
npm run start:dist
```

## Rotas disponiveis

### GET `/teams`

Retorna todas as equipes cadastradas.

Exemplo:

```json
{
  "teams": [
    {
      "id": 1,
      "name": "McLaren",
      "base": "Woking, United Kingdom"
    }
  ]
}
```

### GET `/drivers`

Retorna todos os pilotos cadastrados.

Exemplo:

```json
{
  "drivers": [
    {
      "id": 1,
      "name": "Max Verstappen",
      "team": "Red Bull Racing"
    }
  ]
}
```

### GET `/drivers/:id`

Retorna um piloto pelo `id`.

Exemplo:

```text
http://localhost:3333/drivers/3
```

Resposta:

```json
{
  "driver": {
    "id": 3,
    "name": "Lando Norris",
    "team": "McLaren"
  }
}
```

Se o piloto nao existir:

```json
{
  "message": "Driver Not Found"
}
```

## Observacoes

Os dados estao armazenados em memoria dentro do arquivo `src/server.ts`. Esta API e um projeto inicial para praticar criacao de rotas, uso de TypeScript e organizacao de um servidor com Fastify.
