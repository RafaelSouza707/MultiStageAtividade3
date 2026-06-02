# ==========================
# Estagio 1 - Build
# ==========================
FROM node:20-alpine AS builder

WORKDIR /app

# Copia apenas os arquivos de dependências primeiro
COPY package.json package-lock.json ./

# Instala dependências // ci preferivel ao install
RUN npm ci

# Copia o restante do código
COPY . .

RUN npm run build
# Gera os arquivos estaticos

# ==========================
# Estagio 2 - Produção
# ==========================
# Novo estagio, sem herdar nada
FROM nginx:stable-alpine AS production

# Copia os arquivos gerados pelo build // Em alguns casos ao invés do dist, haverá o "build"
COPY --from=builder /app/dist /usr/share/nginx/html

# Exposição da porta HTTP
EXPOSE 80

# Inicialização do Nginx
CMD ["nginx", "-g", "daemon off;"]