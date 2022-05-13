# Mr. Sales - Parceiros API :)

> Agora é possível cadastrar lead e obter informações da sua loja através da nova API de Parceiros. **Versão: 1.0**

#### Pré requisito

* Ter um login valido na aplicação, para mais informações entre em contato com seu consultor.

##### Homologação
* http://api-homolog.mrsales.com.br

##### Produção
* https://api.mrsales.com.br

#### Example Postman
[Collection Postman com exemplos práticos](https://raw.githubusercontent.com/MrSales/parceiros-api/master/mr.%20Sales%20-%20Parceiros.postman_collection.json)

## Features   

✅ [Autenticação](#autenticação)

✅ [Consulta de Lojas](#lojas)

✅ [Consulta de Bandeiras](#bandeiras)

✅ [Consulta de Tipo de Leads](#tipo-lead-novo---atualizado-em-26112018)

✅ [Catalogo de Veiculos](#catálogo-da-loja)

✅ [Consulta de Leads](#consulta-de-leads-v1)

✅ [Consulta de Horários para Test Drive](#catálogo---horários-disponiveis-para-agendamento)

✅ [Cadastrar Lead](#cadastrar-lead)

✅ [Cadastrar Test Drive](#cadastrar-lead-test-drive)

✅ [Cadastro de Usuários](#usuário---cadastro)

✅ [Atualizar Status do Usuários](#usuário---ativarinativar)

✅ [Cadastro de Cliente](#cadastrar---cliente)

#### Autenticação

##### Para acessar qualquer serviço da API é necessário passar o Token fixo no header. (Caso não possua um token válido, solicitar em suporte@mrsales.com.br)

Exemplo do header

```json
[{"key":"Authorization","value":"{{token}}"}]

```

#### Lojas

Lista de lojas que o usuário tem permissão para cadastrar lead.

* Endpoint: parceiro/lojas
* Content-type: application/json
* Verbo: GET

Request

* Necessário informar token no header

Filtro

* Endpoint: parceiro/lojas?BandeiraID=valor
* Endpoint: parceiro/lojas?marca=X&modelo=Y
* Endpoint: parceiro/lojas?observacao=X
* Endpoint: parceiro/lojas?cidade=Osasco&estado=SP

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

#### Bandeiras

Lista de bandeiras com base nas lojas associadas no token

* Endpoint: parceiro/bandeiras
* Content-type: application/json
* Verbo: GET

Request

1. Necessário informar token no header

Response

```json

{
    "Data": [
        {
            "BandeiraID": 1,
            "Nome": "Hyundai"
        }
    ],
    "Success": true,
    "Message": null
}

```

#### Tipo Lead (novo - atualizado em 26/11/2018)

Lista de tipo de lead com base no seguimentos de atendimento da Concessionárias

* Endpoint: parceiro/tipolead/{contaID}
* Content-type: application/json
* Verbo: GET

Request

1. Necessário informar token no header
2. Necessário informar o ContaID no endpoint

Response

```json

{
    "Data": [
        {
            "TipoLeadID": 999,
            "Descricao": "Consórcio"
        },
		{
            "TipoLeadID": 999,
            "Descricao": "SAC"
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

#### Consulta de Leads (v1)

Lista os 100 ultimos leads gerados 

* Endpoint: parceiro/leads/codigo-loja
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
            "DataCriacao": "2019-07-19T10:45:31.983",
            "LojaID": 0,
            "TipoLeadID": null,
            "Assunto": "Assunto teste....",
            "Mensagem": "mensagem teste....",
            "IsZeroKM": true,
            "UTM_SOURCE": null,
            "UTM_CAMPAIGN": null,
            "Cliente": {
                "Nome": "Cliente Testee",
                "Email": "teste@gmail.com",
                "Telefone": "(11) 9-5463-0464",
                "Celular": "11 0000-0000",
                "CPF": "000.000.000-00",
                "CNPJ": null,
                "IsPJ": null,
                "RazaoSocial": null,
                "Cidade": null,
                "UF": null,
                "AceitaReceberOfertas": null
            },
            "MidiaID": 1,
            "LojaCatalogoID": null
        }
    ],
    "Success": true,
    "Message": null
}

```

#### Catálogo - Horários disponiveis para agendamento

Listar os horários disponível para agendamento de um veículo

* Endpoint: parceiro/catalogo-horario
* Content-type: application/json
* Verbo: POST

Request

1. Necessário informar token no header
2. Body 

```json

{
   "LojaID": 0,
   "LojaCatalogoID": 0,
   "Dia": "2018-10-08"
}
```

Response

```json

{
    "Data": [
        "08:00",
        "09:00",
        "09:30",
        "10:00"
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
2. Os campos vazio (NULL) não são obrigatórios, mas caso seja exigência do cliente essas informações, deve ser preenchido para sair no cadastro e relatórios.

Request

```

{
  "LojaID": 1,
  "Cliente": {
    "Nome": "Fulano",
    "Email": "fulano@mrsales.com.br",
    "Telefone": null,
    "Celular": "11 00000-0000",  
    "Cidade": null,          
    "UF": null,                 
    "CPF":  null,    
    "IsPJ": null,             
    "RazaoSocial": null,         
    "CNPJ": null, 
    "DataNascimento": "yyyy-MM-dd",
    "AceitaReceberOfertas": true,
    "IsPossuoCarroMarca": false,
  },
  "Assunto": "Teste Parceiro",
  "Mensagem": "Teste parceiro msg",
  "MidiaID": 1,
  "LojaCatalogoID": null,      
  "IsZeroKM": false,
  "TipoLeadID": null,        
  "UTM_CAMPAIGN": null,      
  "UTM_SOURCE": null,          
  "UTM_CONTENT": null,            
  "UTM_MEDIUM": null,            
  "UTM_TERM": null            
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

```json

{
  "LojaID": 0,
  "DataHoraAgendamento": "2018-08-30 10:20",
  "Cliente": {
    "Nome": "Fulano",
    "Email": "fulano@mrsales.com.br",
    "Telefone": "11 0000-0000", //opcional
    "Celular": "11 00000-0000",  //opcional
    "CPF": "000.000.000-00",    //opcional
    "Cidade": "Osasco",         //opcional
    "UF": "SP"                  //opcional
  },
  "MidiaID": 0,
  "LojaCatalogoID": 0,
  "UTM_CAMPAIGN": null,           //opcional ex.conheca-novo-carro
  "UTM_SOURCE": null,           //opcional   ex. UOL, Globo, Google Display, Facebook ads
  "UTM_CONTENT": null,           //opcional  
  "UTM_MEDIUM": null,           //opcional   
  "UTM_TERM": null           //opcional   
}

```

Response

```json
{
    "Data": CODIGO_LEAD_GERADA,
    "Success": true,
    "Message": null
}

```

#### Usuário - Cadastro

* Endpoint: parceiro/usuario
* Content-type: application/json
* Verbo: POST

*Obs: necessário solicitar permissão de cadastrar usuário no token.

Request

1. Necessário informar token no header

Request

```json
{
  "Nome": "TesteApi1",
  "Email": "testeapi1@teste.com",
  "Login": "testeapi",
  "Senha": "xxxx",
  "Visualiza0KM": true,
  "VisualizaSeminovos": true,
  "Lojas": [0] //informar o código da loja que deseja liberar o acesso
}

```

Response

```json

{
    "Data": 0,
    "Success": true,
    "Message": ""
}

```

#### Usuário - Ativar/Inativar

* Endpoint: parceiro/usuario/status
* Content-type: application/json
* Verbo: POST

Request

1. Necessário informar token no header

Request

```text
{
  "Login": "",  //Login do Usuário no mrsales
  "Status": false
}

```

Response

```json

{
    "Data": 0,
    "Success": true,
    "Message": ""
}

```

### Cadastro de cliente

* Endpoint: parceiro/cliente/[código da loja]
* Content-type: application/json
* Verbo: POST

Request

1. Necessário informar o token no header
2. Necessário informar o [código da loja] no endpoint
3. Os campos vazio (NULL) não são obrigatórios, mas caso seja exigência do cliente essas informações, deve ser informadas no request.

*Body* 
```json
{
    "Nome": "Sample" ,
    "CPF": "67306839020",
    "Email": "sample@test.com",
    "Telefone": null,       
    "Celular": null,        
    "IsPJ": false,          
    "CNPJ": null,           
    "RazaoSocial": null,    
    "Cidade": null,         
    "UF": null,             
    "Logradouro": null,     
    "Numero": null,         
    "Complemento": null     
}
```

Response

```json

{
    "Data": "41a4cfac-04d4-4734-9b69-b8b19c545443", // código do processamento
    "Success": true, //status se foi recebido com sucesso
    "Message": "cliente adicionado a fila de processamento" //mensagem de retorno
}

```

Response 
> Caso não seja possível processar o cadastro, a API retorna uma mensagem de erro, mas sempre o StatusCode é 200. (exemplo de retorno a baixo)

```json

{
    "Data": null,
    "Success": false,
    "Message": {
        "Erros": [
            {
                "Campo": "Email",
                "Mensagem": "obrigatório informar e-mail"
            }
        ]
    }
}
```

Webhook

> Para receber as notificações sobre o andamento do cadastro é necessário abrir um ticket em suporte@mrsales.com.br e informar a URL que devemos enviar as notificações

Exemplo de retorno

```json

{
    "Hash":"0994a13d-bf7f-4e31-8c8a-6b73286cb4ee",
    "Data":4654584,
    "Status":true,
    "Message":"Cadastro realizado com sucesso"
}

```



dúvidas ou problemas relacionadas API suporte@mrsales.com.br



