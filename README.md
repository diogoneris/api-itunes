# O Projeto
A proposta da criação do projeto visa atender o desafio elaborado pela equipe do InfoGlobo para testar os conhecimentos e habilidades em desenvolvimento backend. O projeto foi desenvolvido com objetivo para efetuar o CRUD persistindo em um banco de dados MySQL, utilizando como a base os dados obtidos a partir de consulta a API do Itunes. (https://affiliate.itunes.apple.com/resources/documentation/itunes-store-web-service-search-api/#searchexamples)

## Tecnologias Utilizadas

- Python na versão 3.9.1
- Framework Flask
- Docker Desktop for Windows
- Docker Compose
- Banco de Dados MySQL na versão 8.0

## Instalação

Faz-se necessário utilizar para o projeto o Docker Desktop for Windows e Docker Compose instalados na máquina.

Através da linha de comando via shell deve-se clonar o repositório:

```shell
git clone https://github.com/diogoneris/api-itunes.git
cd api-itunes
```

O ponto de atenção é importante manter a seguinte estrutura dos arquivos. Caso contrário, o `docker-compose` pode não funcionar.
  
    api-itunes
    └── app
    │    ├── app.py
    │    ├── db_connect.py
    │    ├── Dockerfile
    │    ├── helpers.py
    │    ├── main.py
    │    ├── requirements.py
    │    └── test_helpers.py
    └── db
    │    └── init.sql
    ├── docker-compose.yml
    └── README.md

Logo após fazer o download dos arquivos do repositório api-itunes, digitar a linha de comando abaixo para criar as imagens e os containers.

```shell
docker-compose up
```

Logo após o comandi os containers encontraram em execução. O sistema operacional utilizado no desenvlvimento foi o Windows 10 acessando a API pelo `localhost:3000`. 
Para as máquinas virtuais Windows geralmente o IP `192.168.99.100` é o default, mas caso não funcione tera que pega o IP correto da máquina


## Utilizando a API

Ao utilizar a API pela primeira vez, o banco de bados será inicializado sem dados, apenas com a estrura das tabelas.

O primeiro passo então é adicionar algum artista ao BD. Para isso, pode-se usar comandos como `curl` ou programas específicos para este fim como `Postman` e `Insomnia`.

Com essas ferramentas é possível fazer os requests corretamente e incluir o `body` do request corretamente quando necessário.

Exemplos de usos podem ser vistos no link para a documentação no Postman:

https://documenter.getpostman.com/view/10132901/SWT5j1Zc

## Endpoints
Com o container rodando no Docker é possível fazer chamadas a API utilizando os endpoints documentados em:

https://documenter.getpostman.com/view/10132901/SWT5j1Zc

Mais informações sobre como funciona a lógica da API também se encontram no link acima.

## Testes Unitários
O projeto também conta com um arquivo para testes unitários, chamado `test_helpers.py`, que pode ser encontrado dentro da pasta `app`.

Para rodar os testes basta usar o comando:

```shell
python test_helpers.py #Realiza testes unitários
```


