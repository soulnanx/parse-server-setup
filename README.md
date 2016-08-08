# parse-server
Como configurar o parse-server

<h2>Parse-server com docker</h2>
- clone o parse-server-setup
  - ```git clone git@github.com:soulnanx/parse-server-setup.git```
- crie a imagem do parse-server e parse-server dashboard
  - na pasta build-images/parse-server execute ```docker build -t parse-server .```
  - na pasta build-images/parse-dashboard execute ```docker build -t parse-dashboard .```
   
- escolha a arquitetura
  - multi-parse-server: <i>varios projetos parse-server rodando e um dashboard administrando</i>
  - single-parse-server: <i>um parse-server para um dashboard</i>
   
<h3>multi-parse-server</h3>
- vá até a pasta multi-parse-server e adicione suas configurações de push-notification e configurações do seu projeto no arquivo parse-server-config.json
  - para cada parse-server novo, você terá que criar um novo parse-server-config.json ex:parse-server-config2.json
- no docker-compose preencha as variaveis com as informações do seu projeto
  - para cada parse-server novo, você terá que criar um bloco de parse-server e apontar no ```command: parse-server parse-server-config.json``` o arquivo que você criou no passo anterior 
- suba o servidor com ```docker-compose up -d```
- obs: esteja com o container do mongo já em execução

<h3>single-parse-server</h3>
- vá até a pasta single-parse-server e adicione suas configurações de push-notification no arquivo parse-server-config.json
- no docker-compose preencha as variaveis com as informações do seu projeto
- suba o servidor com ```docker-compose up -d```
- obs: esteja com o container do mongo já em execução

<h2>Parse-server com npm</h2>

<h4>Caso tenha algum problema com o npm no Mac OSX</h4>
```npm update npm -g```

<h4>Instalar o parse-server e o mongo(validar)</h4>
```npm install -g parse-server mongodb-runner```

<h4>Instalar o parse-dashboard</h4>
```npm install -g parse-dashboard```

<h4>Exemplo de arquivo de configurações do parse-server (parse-server-config.json)</h4>
Mais detalhes em: [github parse-server push](https://github.com/ParsePlatform/parse-server/wiki/Push)
```json
  {
    "appId": "app.mto.loko",
    "masterKey": "chave",
    "databaseURI" : "mongodb://host:port/dbName",
    "push": {
      "android": {
        "senderId": "sender",
        "apiKey": "server-key"
      },
      "ios": {
        "pfx": "/file/path/to/XXX.p12",
        "passphrase": "", 
        "bundleId": "",
        "production": false
      }
    }
  }
```
  
<h4>Exemplo de arquivo de configurações do parse-dashboard (parse-dashboard-config.json)</h4>
```json
  {
    "apps": [
      {
        "serverURL": "http://localhost:1337/parse",
        "appId": "app.mto.loko",
        "masterKey": "senha",
        "appName": "Super app"
      }
    ],
    "users": [
       {
         "user":"user1",
         "pass":"pass1",
         "apps": [{"appId": "app.mto.loko"}, {"appId": "app.mto.loko2"}]
       },
       {
         "user":"user2",
         "pass":"pass2",
         "apps": [{"appId": "app.mto.loko"}]
       }  
     ]
  }
```

<h4>Subir o servidor</h4>
  - <i>mongodb-runner</i> ```mongodb-runner start```  
  - <i>parse-server</i> ```<VERBOSE=1 para logs> parse-server parse-server-config.json```  
  - <i>parse-dashboard</i> ```parse-dashboard --config parse-dashboard-config.json``` 

Essas informações foram retiradas do github oficial do [Parse-Platform](https://github.com/ParsePlatform)
