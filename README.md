# parse-server
Como configurar o parse-server

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
  
<h4>Exemplo de arquivo de configurações do parse-server</h4>
```json
  {
    "apps": [
      {
        "serverURL": "http://localhost:1337/parse",
        "appId": "app.mto.loco",
        "masterKey": "senha",
        "appName": "Super app"
      }
    ],
    "users": [
     {
       "user":"user1",
       "pass":"pass1",
       "apps": [{"appId": "app.mto.loco"}, {"appId": "app.mto.loco2"}]
     },
     {
       "user":"user2",
       "pass":"pass2",
       "apps": [{"appId": "app.mto.loco"}]
     }  ]
  }
```

<h4>Subir o servidor</h4>
  - <i>parse-server</i> ```<VERBOSE=1 para logs> parse-server parse-server-config.json```  
  - <i>parse-dashboard</i> ```parse-dashboard --config parse-dashboard-config.json``` 

Essas informações foram retiradas do github oficial do [Parse-Platform](https://github.com/ParsePlatform)
