FROM node:lts-alpine

# Instala um servidor http simples para servir conteúdo estático
RUN npm install -g http-server

# Faz da pasta 'app' o diretório atual de trabalho
WORKDIR /app

# Copia os arquivos 'package.json' e 'package-lock.json' (se disponível)
COPY package*.json ./

# Instala dependências do projeto
RUN npm install

# Copia arquivos e pastas para o diretório atual de trabalho (pasta 'app')
COPY . .

# Compila a aplicação de produção com minificação
RUN npm run build

EXPOSE 8000
CMD [ "http-server", "dist" ]