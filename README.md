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

Logo após o comandi os containers encontraram em execução. O sistema operacional utilizado no desenvlvimento foi o Windows 10 acessando a API pelo `localhost:5000`. 
Para as máquinas virtuais Windows geralmente o IP `192.168.99.100` é o default, mas caso não funcione terá que pegar o IP correto da máquina


## Utilizando a API

Ao utilizar a API pela primeira vez, o banco de bados será inicializado sem dados, apenas com a estrura das tabelas.

O primeiro passo então é adicionar algum artista ao BD. Para isso, pode-se usar comandos como `curl` ou programas específicos para este fim como `Postman` e `Insomnia`.

Com essas ferramentas é possível fazer os requests corretamente e incluir o `body` do request corretamente quando necessário.

Exemplos de usos podem ser utilizados:

* GET Page Not Found
```shell
192.168.99.100:5000/
```
Request feito para um caminho que não existe.

Example Request

curl --location --request GET '192.168.99.100:5000/' \
--data-raw ''

Example Response

"Page not found."


* POST Adicionar Artista
```shell
192.168.99.100:5000/artistas
```
Request para adicionar o artista ao Banco de Dados.

Example Request

curl --location --request POST '192.168.99.100:5000/artistas' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Joe Jonas"
}'

Example Response

"Added successful."

* POST Adicionar Álbum a Artista
```shell
192.168.99.100:5000/artistas/1/albuns
```
Request para adicionar album a um artista identificado pelo ID do Banco de Dados.

Example Request

curl --location --request POST '192.168.99.100:5000/artistas/2/albuns' \
--header 'Content-Type: application/json' \
--data-raw '{
	"name" : "Album"
}'

Example Response

"Artist not on DB."

* POST Adicionar Musica a Álbum
```shell
192.168.99.100:5000/albuns/2/musicas
```
Request para adicionar música a um album identificado pelo ID do Banco de Dados.


Example Request

curl --location --request POST '192.168.99.100:5000/albuns/1/musicas' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Musica"
}'

Example Response

"Album not on DB."

* PUT Alterar nome de Artista de ID
```shell
192.168.99.100:5000/artistas/9
```
Request para alterar o nome de artista identificado pelo ID do Banco de Dados.


Example Request

curl --location --request PUT '192.168.99.100:5000/artistas/1' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Novo Nome Artista"
}'

Example Response

"Artist not on DB."

* DEL Deletar todos os Artistas
```shell
192.168.99.100:5000/artistas
```

Example Request

curl --location --request DELETE '192.168.99.100:5000/artistas'

Example Response

"Deletion successful"

* DEL Deletar todos os Álbuns

```shell
192.168.99.100:5000/albuns
'''

Request para deletar todos os albuns do Banco de Dados.

Example Request

curl --location --request DELETE '192.168.99.100:5000/albuns'

Example Response

"Deletion successful"


* GET Todos os artistas

```shell
192.168.99.100:5000/artistas
```

Request que retorna todos os artistas que estão no Banco de Dados.

Example Request

curl --location --request GET '192.168.99.100:5000/artistas'

Example Response

[
  {
    "idArtist": 1,
    "idArtistItunes": 162092469,
    "nameArtist": "Joe Jonas"
  },
  {
    "idArtist": 2,
    "idArtistItunes": null,
    "nameArtist": "Testerr"
  }
]

* GET Todos os álbuns

```shell
192.168.99.100:5000/albuns
```

Request que retorna todos os albuns que estão no Banco de Dados.

Example Request

curl --location --request GET '192.168.99.100:5000/albuns'

Example Response

[
  {
    "explicit": "notExplicit",
    "genre": "Dance",
    "idAlbum": 2,
    "idAlbumItunes": 1402144828,
    "idArtistAlbum": 1,
    "nameAlbum": "I See Love (feat. Joe Jonas) [From \"Hotel Transylvania 3\"] - Single",
    "nameArtistAlbum": "Jonas Blue",
    "trackCount": 1
  },
  {
    "explicit": "notExplicit",
    "genre": "Soundtrack",
    "idAlbum": 3,
    "idAlbumItunes": 1408399412,
    "idArtistAlbum": 1,
    "nameAlbum": "It's Party Time (From the \"Hotel Transylvania 3\" Original Motion Picture Soundtrack) - Single",
    "nameArtistAlbum": "Joe Jonas",
    "trackCount": 1
  },
  {
    "explicit": "notExplicit",
    "genre": "Pop",
    "idAlbum": 4,
    "idAlbumItunes": 1444618546,
    "idArtistAlbum": 1,
    "nameAlbum": "One Chance to Dance (feat. Joe Jonas) - Single",
    "nameArtistAlbum": "Naughty Boy",
    "trackCount": 1
  },
  {
    "explicit": "notExplicit",
    "genre": "Pop",
    "idAlbum": 5,
    "idAlbumItunes": 1444619484,
    "idArtistAlbum": 1,
    "nameAlbum": "One Chance to Dance (feat. Joe Jonas) [Remixes] - Single",
    "nameArtistAlbum": "Naughty Boy",
    "trackCount": 3
  },
  {
    "explicit": "notExplicit",
    "genre": "Pop",
    "idAlbum": 6,
    "idAlbumItunes": 1444854949,
    "idArtistAlbum": 1,
    "nameAlbum": "One Chance To Dance (Acoustic) [feat. Joe Jonas] - Single",
    "nameArtistAlbum": "Naughty Boy",
    "trackCount": 1
  },
  {
    "explicit": "cleaned",
    "genre": "Pop",
    "idAlbum": 7,
    "idAlbumItunes": 1457234843,
    "idArtistAlbum": 1,
    "nameAlbum": "Fastlife",
    "nameArtistAlbum": "Joe Jonas",
    "trackCount": 12
  }
]



## Endpoints
Com o container rodando no Docker é possível fazer chamadas a API utilizando os endpoints documentados em:

https://documenter.getpostman.com/view/10132901/SWT5j1Zc

Mais informações sobre como funciona a lógica da API também se encontram no link acima.

## Testes Unitários
Há o teste unitário chamado `test_helpers.py`, que pode ser encontrado dentro da pasta `app`.

```shell
python test_helpers.py #Realiza testes unitários
```


