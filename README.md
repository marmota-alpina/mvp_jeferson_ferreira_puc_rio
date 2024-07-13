# MVP Jeferson Ferreira da Silva

## Projetos de MVP
- [x] API de Endereços https://github.com/marmota-alpina/address-service.git
- [x] API de Frete https://github.com/marmota-alpina/jedex_api.git
- [x] Frontend Frete https://github.com/marmota-alpina/jedex-ui.git
- [x] API de Produtos https://github.com/marmota-alpina/product-hub.git
- [x] Frontend de Produtos https://github.com/marmota-alpina/product-hub-ui.git
- [x] Integração de Produtos com Fakestore API

## Execução do Projeto

### Pré-requisitos
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Portas 3000 e 4000 disponíveis para o frontend
- Portas 80 para o backend e 8081 para o Traefik (proxy reverso)
- Portas 5433, 5434 e 5435 para o banco de dados postgres


### Clonar o repositório
```bash 
git clone https://github.com/marmota-alpina/mvp_jeferson_ferreira_puc_rio.git
```

### Executar o projeto
```bash
cd mvp_jeferson_ferreira_puc_rio
docker-compose up --build
```

### Acessar o frontend
- [http://localhost:3000](http://localhost:3000) Configurar Contrato de Frete
- [http://localhost:4000](http://localhost:4000) Gerenciar Produtos

### Acessar o backend
- [http://localhost:80](http://localhost/address) API de Endereços
- [http://localhost:80](http://localhost/jedex) API de Frete
- [http://localhost:80](http://localhost/product-hub) API de Produtos

### Accessar o traefik
- [http://localhost:8081](http://localhost:8081) Dashboard do Traefik

## Limpando o ambiente
Para limpar o ambiente, execute o comando abaixo:
```bash
  docker-compose down
```
```bash
  docker rm -f $(docker ps -aq)
  docker rmi -f $(docker images -q)
  docker volume rm $(docker volume ls -q)
```

