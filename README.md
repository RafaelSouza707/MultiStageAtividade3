# MultiStageAtividade3

## Execute o seguinte comando para inicializar a criação dos containers e para ter o projeto pronto para produção

`docker build -t minha-app-testes .`

## Execute o seguinte comando para inicilizar a produção do projeto

`docker run -d -p 8080:80 minha-app-testes`


## Respostas sobre: Perguntas de reflexão

### Responda brevemente após concluir o Dockerfile:
### 1. Qual é o benefício de copiar package.json e package-lock.json antes do restante do código-fonte? Como isso se relaciona com o sistema de cache de camadas do Docker?

#### Docker usa cache por camadas. Ao copiar primeiro o package.json e package-lock.json mudanças em arquivos da aplicação não obrigam o docker a reinstalar todas as dependências, assim os builds ficam mais rapidos.

### 2. O que aconteceria com o tamanho final da imagem se utilizássemos um único estágio com node:20 e simplesmente copiássemos os arquivos estáticos para a pasta do Nginx dentro da mesma imagem?

#### Ela conteria Node.js completo, npm, dependências de desenvolvimento, cache de intalação, arquivos temporários e ficaria significativamente maior

### 3. O Nginx precisa do Node.js instalado para servir os arquivos estáticos da aplicação React? Justifique sua resposta em relação ao conceito de multi-stage build.

#### Não, pois a aplicação após convertida em arquivos estáticos conteria apenas: HTML, CSS, JS, imagens e outros assets, nada disso precisa do Node.js.
