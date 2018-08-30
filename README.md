# Mr. Sales - Parceiros API :)

> Agora é possível cadastrar lead e obter informações da sua loja através da nova API de Parceiros. **Versão: 1.0**

#### Pré requisito

* Ter um login valido na aplicação, para mais informações entre em contato com seu consultor.

##### Homologação
* http://api-homolog.mrsales.com.br

##### Produção
* https://api.mrsales.com.br


#### Autenticação

Para acessar qualquer serviço da API é necessário passar o Bearer Token no header, todos os tokens gerados expira em 24horas.

* Endpoint: parceiro/autenticar
* Content-type: application/json
* Verbo: POST

Request

```json

{
  "Login": "XXXXX",
  "Senha": "XXXXX",
  "CNPJ": "XX.XXX.XXX/XXXX-XX"
}

```

Response

```json

{
    "Data": {
        "Token": "XXXXXX",
        "Usuario": {
            "UsuarioID": 0,
            "Nome": "Emerson Jose",
            "Email": "emerson@mrsales.com.br"
        }
    },
    "Success": true,
    "Message": null
}

```

#### Lojas

Lista de lojas que o usuário tem permissão para cadastrar lead.

* Endpoint: parceiro/lojas
* Content-type: application/json
* Verbo: GET

Request

* Necessário somente passar o token no header

Response

```json

{
    "Data": [
        {
            "LojaID": 1,
            "NomeFantasia": "Mr. Sales",
            "CNPJ": "XX.XXX.XXX/XXXX-XX",
            "RazaoSocial": "Mr. Sales",
            "BandeiraDescricao": "Hyundai",
            "Enderecos": [
                {
                    "LojaEnderecoID": 0,
                    "LojaID": 0,
                    "CEP": "04537-080",
                    "Logradouro": "Rua Comendador Miguel Calfat",
                    "Numero": "128",
                    "Complemento": "8º andar",
                    "Bairro": "Vila Nova Conceição",
                    "Estado": "SP",
                    "Cidade": "São Paulo",
                    "Latitude": 23.5917124,
                    "Longitude": -46.6760362
                }
            ],
            "Contatos": [
                {
                    "LojaID": 0,
                    "LojaContatoID": 0,
                    "Celular": "",
                    "Email": "contato@mrsales.com.br",
                    "Fax": "",
                    "Nextel": "",
                    "Telefone": "11 3796-6708",
                    "WhatsApp": "00 00000-0000",
                    "Nome": "Mr. Sales",
                    "WhatsAppRevisao": "00 00000-0000",
                    "TelefoneRevisao": "00 0000-0000",
                    "TelefonePosVenda": "00 0000-0000"
                }
            ]
        }
    ],
    "Success": true,
    "Message": null
}

```

#### Catálogo da Loja

Listar o catálogo de veiculos da loja

* Endpoint: parceiro/catalogo/codigo-loja
* Content-type: application/json
* Verbo: GET

Request

1. Necessário informar token no header
2. Substituir codigo-loja do endpoint pelo Id da Loja

Response

```json

{
    "Data": [
        {
            "LojaCatalogoID": 0,
            "Marca": "Hyundai",
            "Modelo": "Creta",
            "Versao": "Creta 1.6 Attitude",
            "TestDriveSegSexta": true,
            "TestDriveSegundaSextaInicio": "10:00",
            "TestDriveSegundaSextaFim": "19:00",
            "TestDriveSabado": true,
            "TestDriveSabadoInicio": "10:00",
            "TestDriveSabadoFim": "15:00",
            "TestDriveDomingo": true,
            "TestDriveDomingoInicio": "10:00",
            "TestDriveDomingoFim": "15:00",
            "TestDriveDuracao": 20
        }
    ],
    "Success": true,
    "Message": null
}

```

#### Cadastrar Lead

* Endpoint: parceiro/lead
* Content-type: application/json
* Verbo: POST
* Necessário solicitar o cadastramento da MidiaID do Portal/Site em suporte@mrsales.com.br

Request

1. Necessário informar token no header

Request

```

{
  "LojaID": 1,
  "Cliente": {
    "Nome": "Fulano",
    "Email": "fulano@mrsales.com.br",
    "Telefone": "11 0000-0000", //opcional
    "Celular": "11 00000-0000", //opcional
    "CPF": "030.848.781-88",   //opcional
    "Cidade": "Osasco",        //opcional
    "UF": "SP"                 //opcional
  },
  "Assunto": "Teste Parceiro",
  "Mensagem": "Teste parceiro msg",
  "MidiaID": 0,
  "LojaCatalogoID": 0
}

```

Response

```
{
    "Data": CODIGO_LEAD_GERADA,
    "Success": true,
    "Message": null
}

```

#### Cadastrar Lead Test Drive

* Endpoint: parceiro/testdrive
* Content-type: application/json
* Verbo: POST
* Necessário solicitar o cadastramento da MidiaID do Portal/Site em suporte@mrsales.com.br

Request

1. Necessário informar token no header

Request

```

{
  "LojaID": 0,
  "DataHoraAgendamento": "2018-08-30 10:20",
  "Cliente": {
    "Nome": "Fulano",
    "Email": "fulano@mrsales.com.br",
    "Telefone": "11 996528896", //opcional
    "Celular": "11 996528896",  //opcional
    "CPF": "030.848.781-88",    //opcional
    "Cidade": "Osasco",         //opcional
    "UF": "SP"                  //opcional
  },
  "MidiaID": 0,
  "LojaCatalogoID": 0
}

```

Response

```
{
    "Data": CODIGO_LEAD_GERADA,
    "Success": true,
    "Message": null
}

```

> dúvidas ou problemas relacionadas API suporte@mrsales.com.br