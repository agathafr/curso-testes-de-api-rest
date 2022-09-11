# Testes de API Rest 

Técnicas, estratégias e abordagens para teste de API Rest.

## Aprender a manipular API Rest

- Introdução a APIs Rest
- Service, Repository e Controller
- Request & Response
- Headers
- Parâmetros
- Autenticação e Autorização 
- Insomnia (Ferramenta para manipulação de API)
- Postman (Ferramenta para manipulação de API)
- RestAssured (Testa a partir da escrita de script de testes automatizados)

Enviar requisições via GET e via POST, validar as respostas, montar uma requisição, entender como funciona o fluxo não é suficiente para testar uma API, é só saber manipular (usar). Testar envolve o conhecimento de técnicas, estratégias, abordagens de teste voltadas para API Rest, testes funcionais, testes não funcionais.

## Aprender a testar API Rest

- Estratégias de teste de API Rest
- Cobertura de Testes
- Testes Funcionais
- Testes de Performance
- Testes de Compatibilidade
- Mountbank (Mock para simular uma API Rest terceira)
- JSONSSchema (Validar corpo da resposta)
- Leitura de Logs (Entender a causa raiz de problemas encontrados)

## Introdução a APIs Rest - Um estilo de arquitetura 

### O que é

API é uma Interface de programação de aplicações que objetiva expor um produto ou serviço sem que as pessoas que vão consumi-lo conheçam a sua estrutura, implementações internas. Para melhor assimilação do conceito, pode-se fazer uma associação com o de "teste caixa preta", onde o teste é feito observando o exterior e sem ter conhecimento do interior.

As primeiras implementações de API eram locais: bibliotecas disponíveis para download que ao serem baixadas poderiam ser utilizadas a partir de softwares que estavam sendo construídos por quem fez o download. 

A API possui uma interface para uma aplicação. Um site possui uma interface para um usuário. A API espera que outros softwares se comuniquem com ela, enquanto uma UI espera a interação de um usuário. 

Designers usam protocolos e recomendações para criar uma interface mais simples para um usuário, usabilidade. 

Quando se trata de uma API, a característica principal é a interoperabilidade (facilidade de interação, comunicação entre sistemas).

### Compartilhar parte de um software com o mundo

Ao compartilhar uma funcionalidade de busca com um usuário, ele interagiria com ela a partir da interface, com cliques e digitação. Quando o compartilhamento for feito para um sistema, existem protocolos(ex.: SOAP) e arquiteturas(ex.: REST) que padronizam a forma que ele deve ocorrer a fim de alcançar a interoperabilidade (comunicação simples entre diferentes sistemas).

Um software, ao se conectar com uma API Rest, sabe o estilo de envio de requisições, verbos e métodos que podem ser utilizados e sabe as respostas esperadas que serão retornadas devido ao conhecimento do padrão do modelo arquitetural (rest).

### Testando uma API 

O teste de API não deve ser feito apenas verificando se a resposta a uma requisição é a esperada porque não abrange a verificação da forma de implementação (que deve seguir a especificação do modelo arquitetural escolhido), por exemplo.

### Vantagens que a tornam popular

API Rest é amplamente utilizada nos dias de hoje devido a algumas características que a tornam mais leve 

- Troca de arquivos feita no formato JSON
- Troca de requisições e intenção das respostas expressada através dos métodos GET, POST, DELETE etc.
- A troca de informações geralmente é feita através de um requisição http para API Rest, que ao receber a requisição, faz um processamento e devolve uma resposta para um software terceiro que pode usar a resposta para processar e renderizar informações para ele. 

### Modelos
Dois modelos de implementação de API bem conhecidos são SOAP e REST.

### Ao longo do curso serão apresentadas 

As características que fazem parte de APIs Rest:
- Forma de envio de requisições
- Forma de recebimento de respostas
- Interação com cabeçalhos e autenticações

## Service, Repository e Controller 

Atrás de uma API existe um software conhecido como back-end, a solução construída, e à frente, existe a interface gráfica pela qual o usuário interage com o software.

No back-end tem coisas comuns a diferentes softwares como, por exemplo, um local que guarda as regras de negócio e outro que guarda regras e mecanismos de contato entre as regras de negócio e persistência de dados. 

Service e repository são dois componentes comuns na arquitetura de API Rest.

"Service" é uma camada dentro do back-end da aplicação que normalmente armazena as regras de negócio.

"Repository" é uma camada da aplicação responsável por intercambiar as informações entre as regras de negócio ou banco de dados. 

Antes de reportar um bug ao desenvolvedor o ideal é consultar no log se a inconsistência está no service ou no repository. 

A camada service chama a camada repository que retorna as informações necessárias ao desenvolvimento da funcionalidade que implementa uma regra de negócio. A controller contém as anotações, implementações, retorno do status code e response (em json), necessários para a publicação da funcionalidade remotamente viabilizando o acesso de serviços externos/terceiros e o consumo/consulta dos dados fornecidos. 

## O que são Request e Response

O que acontece por debaixo dos panos para que as caracteristica da API Rest estejam disponíveis e funcionais. 

API Rest expões os serviços ou repositorys que estão no back-end para o mundo através de uma API Remota. Se não fosse uma api desse tipo, seria necessário compilar o código e enviar para outras pessoas que queiram fazer uso de seus recursos. 

O controlador é a interface entre o mundo e os services.

Quem desejar fazer uso da API Rest deverá fazer um GET, uma requisição. Uma requisição é uma consulta para uma URL que pode ou não requerer um parâmetro. 

### Como um software terceiro envia uma requisição para uma API Rest

API Rest abstrai o que existe no back-end para que ele consuma as informações e retorne os dados para o cliente que faz a requisição. 

OBS: Pesquisar como uma API funciona e os conceitos por detrás dela. É preciso entender profundamente o objeto de teste. O que compõe uma requisição? E uma resposta?

Curl possibilita o envio de requisições via HTTP. 

Client é um software que faz requisições a API Rest querendo consumir as informações dela. Ele não conhece a implementação da API. A implementação é abstraída e é disponibilizada para os softwares de externos, uma camada que contém recomendações REST, configurando-a como uma API Restfull.

A definição do que é necessário para buscar viagens, no caso da API de exemplo, é um usuário com credenciais válidas e que seja do tipo Usuário. 

Gerar um token referente ao usuário válido. Token é uma série de caracteres alfanuméricos que possibilita o acesso a um endpoint. 

Para testar o endpoint pede credencias válidas e que seja do tipo Usuário. O time vai fornecer um token para possibilitar a execução dos testes. Em posse do token é possível manusear a API Rest (enviar uma requisição via http que seja direcionada exatamente para o método que retorna todas as viagens ou apenas algumas).

Client externo -> Pode ser uma aplicação com interface gráfica ou uma outra API que queira fazer uso da API que está disponível de maneira remora. 

### Enviando e Recebendo requisições via terminal 

#### Comando que chama a aplicação que serve para envio de requisições e recebimento de respostas
```bash
curl  
``` 
#### Como montar o comando da requisição
-X + método que quer chamar + url que quer ter acesso ao endpoint + /api + uri endpoint + -H 'Authorization: '

```bash
curl -X GET http://localhost:8089/api/v1/viagens -H 'Authorization: token'
```

É possível encontrar o endereço na aba "Local" e também na documentação de APIs Rest escrita no formato Swagger. 

/api é um endereço padrão da API de exemplo do Antônio.

As informações de endereço são buscadas no Swagger.

Ao teclar 'enter' a requisição é enviada e a resposta aparece logo abaixo entre chaves {}. 

Na requisição não foram enviadas as credenciais e por isso retornou um código de erro. 

O site JSONFORMATTER melhora a visibilidade da response em relação ao terminal. 

### Testes em API

Pensar nas possibilidades que podem ocorrer dentro do endpoint, dentro dos services ou repositorys chamados pelos services. Observar só as requisições e retorno deles, ignora as demais camadas que precisam ser testadas também. Existem várias possibilidades para além do Controller. Podem ocorrer variações no Services ou Repositorys. Técnicas e estratégias de testes podem ser aplicadas no Controller para avaliar outros caminhos que não o "caminho feliz" que fica explicito na implementação. Poderiam ser testadas várias requisições simultâneas ao endpoint, enviar requisição com token de administrador em detrimento de um de usuário, enviar parâmetros que não os listados, colocar valores muito grandes para saber se a API saberia lidar com isso.

Exemplo do professor: Pessoa simulando um software terceiro que quer buscar viagens que estão registradas na API Rest. Enviou uma requisição via GET (que caiu no controlador) para a uri do endpoint, com um token de usuário, entrou dentro do método, passou informações para dentro dele, o método chamou o services que chamou o repository que buscou no banco de dados, trouxe as informações que devolveu pro services que devolveu pro controler e o controlador foi responsável por converter a resposta para json. 

Validar se funcionalmente trouxe os dados esperados e a estrutura. Lista, objetos, se atributos são do tipo inteiro, ou string e se for, se está entre aspas etc. 

## Como usar Headers, Swagger e Verbos em APIs Rest

### O que são Headers?

Uma parte dentro da requisição que será enviada ao servidor que carrega informações técnicas que ajudam ele a processar o que está sendo enviado na requisição. 

Quais informações? 

- Content type: Tipo de dado enviado dentro da request
Exemplo: Resquisições que registram informações precisam definir o tipo como JSON ou XML
- Autenticação: Define uma authorization e coloca um token para o servidor saber quem está fazendo a request. 

Swagger é uma documentação da interface, formas de interagir com a API Rest construída pelo Antônio, nesse caso. Não é a documentação completa. Podem existir documentações complementares como diagrama de sequência, caso de uso, atividades. O swagger vai mostrar as características da interface de programação de aplicações. 

#### Link para acessar a documentação da API

http://localhost:8089/api/swagger-ui.html

Uma recomendação para definir endpoints é usar um substantivo no plural

POST cria dados ou envia informações sensíveis criptografadas (caso a aplicação utilize o protcolo https)
GET busca dados
PUT atualiza
DELETE apaga

Swagger mostra método, endpoint e conteúdo da requisição (informações que precisam ser enviadas ao fazer a requisição) e a estrutura da resposta que será retornada.

## Resumão até então
- Conhecer o objeto de teste ajuda a ter clareza das técnicas e estratégias de teste a serem aplicadas nele;
- API Rest é uma camada de interface que abstrai a inteligência que contém no back-end
- A interface (API) pode seguir recomendações ou protocolos destintos. Ao usar rest, as orientações e recomendações do rest são seguidas para testar uma API Restfull (API que implementa as recomendações Rest)
- Para interagir com uma API Rest é preciso enviar requisições para obter respostas
- Existem métodos e endpoints para onde devem ser enviadas requisições. Estas podem ter cabeçalho e corpo. 

## Autenticação e Autorização em APIs Rest
Ao decidir fazer uma requisição para cadastrar uma viagem, é preciso verificar na documentação da API o que é obrigatório informar nessa requisição e enviar nela. É preciso informar no header o token para autenticação, caso contrário o retorno vai ser de não estar autenticado, não ser alguém que tem permissão para fazer a requisição (acessar o sistema). Isso porque a API Rest é stateless, não preserva o status como as aplicações web, que guarda a sessão. A cada nova interação é preciso se mostrar alguém que pode ter acesso ao que a requisição irá retornar e uma outra validação, posterior, é de autorização a realizar a ação de que trata a requisição que está sendo feita (ex.: requisição para cadastrar uma viagem).

A autenticação é sobre quem você é e autorização sobre o que você pode ou não fazer. 

É importante identificar para cada operação quem tem o perfil que tem autorização para realizá-la.

## Header, Query, Path e Body: Como usar parâmetros em APIs Rest?

Quais são as formas de enviar dados para uma API Rest?

### 4 Formas:
Através do:

- Header
- Body 
- Query
- Path

```bash
curl -X POST -is http://localhost:8089/api/v1/viagens -d '{ "acompanhante": "Isabele", "dataPartida": "2021-09-11", "dataRetorno": "2022-09-11", "localDeDestino": "Manaus", "regiao": "Norte" }' -H 'Content-Type: application/json' -H 'Authorization: '
```
#### Body

Parâmetro -d usado normalmente em requisições com métodos POST e PUT. Dentro do body é passada uma string, geralmente em formado JSON mas pode ser outros tipos de texto (xml, por exemplo).

```bash
-d '{ "acompanhante": "Isabele", "dataPartida": "2021-09-11", "dataRetorno": "2022-09-11", "localDeDestino": "Manaus", "regiao": "Norte" }'
```

#### Header
Aspas simples, nome: valor.

```bash
-H 'Content-Type: application/json' -H 'Authorization: '
```

#### Query
Após o endpoint colocar uma ? o nome do parâmetro que consta na documentação, =, e o valor a ser enviado. 
Para colocar mais de um parâmetro, é só acrescentar & e seguir a mesma ideia de colocar o nome do parâmetro, =, e o valor. 

```bash
http://localhost:8089/api/v1/viagens(fim do endpoint)?regiao=Norte
```
#### Path

Passado no endpoint após /

```bash
http://localhost:8089/api/v1/viagens/1
```

![image](https://user-images.githubusercontent.com/85461130/189527999-10b47e07-b43a-43e5-b509-706e8d577f1d.png)

## Manipulando APIs Rest com o uso de ferramentas de interface gráfica

### Como usar o Insomnia para Testar APIs Rest

#### Insomnia

Ferramenta de código aberto que objetiva facilitar o design, teste e entrega de APIs Rest

Em Header, é possível usando o "response", buscar informações que estão dentro de outras requests. 

#### Documentação

https://docs.insomnia.rest/

### Como usar o Postman para Testar APIs Rest

### Postman 

Objetiva simplificar cada etapa da construção de uma API e agilizar a colaboração para que você possa criar APIs melhores - mais rápido. 

#### Construção de requisições no Postman

Menu > Colections (guarda coleções de requests(requisições))

Liga o servidor da api (precisa estar ligado para as requisições funcionarem)

```bash
mvn sping-boot:run 
```

A aba "tests" contém os scripts que serão executados após o recebimento da resposta da requisição.

## Como automatizar testes de API Rest com RestAssured usando Java e JUnit

Serão criados scripts de teste automatizado capazes de enviar requisições, receber respostas e realizar asserções nelas. 

#### RestAssured 

Biblioteca para criação de scripts de testes automatizados.

Automação da um feedback rápido após alterações no código, deixando o desenvovledor confiante. 

É um contrato entre a aplicação e quem fez o script, ao parar de funcionar, significa que o contrato foi quebrado e ajustes são necessários. 

#### Arquivo pom.xml

Tem uma tag com todas as dependências que o projeto precisa. Elas são baixadas do site do maven repoditory. 

A dependência do junit será utilizada para estruturar o teste em si. 

O RestAssured da a possibilidade de fazer requisições a APIs Rest e validar suas respostas. 

## Como fazer estratégias de Testes de API Rest 

Estratégias de teste de API Rest = Resquisitos de teste
Existem modelos para estratégias de teste. Variam a depender da plataforma (web, mobile, desktop)

![image](https://user-images.githubusercontent.com/85461130/189539088-14e6fea5-cf2e-4567-bcc0-1efc28043812.png)

Massa - Dado já restrado dentro da aplicação. 
Exemplos: Para buscar detalhes de uma viagem, é preciso que já exista uma viagem registrada; Usuário e senha de usuário comum (não administrador)

Mocks são simuladores de serviços reais que sempre ficam disponíveis apesar de não serem muito complexos. 

Abordagens são formas sistemáticas de testar uma aplicação. 

Permutação: combinar as partições de entrada

![image](https://user-images.githubusercontent.com/85461130/189539818-a86cc710-c117-4e2f-9205-127b3399ccfe.png)
![image](https://user-images.githubusercontent.com/85461130/189539842-75c305d9-10c6-4d60-9f63-bff0f94bd49c.png)
![image](https://user-images.githubusercontent.com/85461130/189539884-8bbd38ac-c264-43bc-95ce-8ee15a213baa.png)
![image](https://user-images.githubusercontent.com/85461130/189539925-87fec4d3-1d0e-4b87-b126-f4761940f7c4.png)

## Como medir a Cobertura de Testes de API Rest?

Análise de Martin Lopez sobre como pode ser calculada a cobertura de testes de APIs com base em inputs e outputs.
Cobertura de testes com base em requisitos: Calcula-se a quantidade de requisitos e testes escritos para cada requisito e a partir disso e entende-se o percentual de cobertura. Ex: Se de 10 requisitos, apenas para 5 foram escritos testes, a cobertura é de 50%.
Ainda existe cobertura com base em riscos, código etc.

Swagger é uma forma de descrever a interface da API Rest. A estratégia de Martin trata de cobrir a interface da API Rest

#### Path
Conta a quantidade de caminhos (paths, uri) e testes escritos para os caminhos

#### Operation coverage  
Uso do método com o endpoint

#### Valor do parâmetro 
Possibilidades de envio de valores. Precisa ter testes para cada um  

### Referências
https://personal.us.es/amarlop/wp-content/uploads/2019/09/Test_Coverage_Criteria_for_RESTful_Web_APIs.pdf

https://medium.com/revista-dtar/como-verificar-a-cobertura-de-testes-da-api-rest-9e2f745564b

## Testes funcionais 

Swagger é uma documentação da interface. Da para visualizar as funcionalidades (representadas pelo controller), em cada controller tem as operações (conjunto de métodos), cada operação tem um método/verbo, ao lado contém o endpoint, dentro do endpoint da para visualizar o que é necessário passar na requisição para consumir o endpoint. É possível visualizar a estrutura das respostas também. 

Essa documentação apenas não basta porque não contém regras de negócio.

Swagger mostra os elementos necessários para interagir com a interface. Como um software pode utilizar a API. 

As regras de negócio podem estar em um caso de uso, diagrama de sequência, num e-mail, na cabeça de alguém.

Testes funcionais geralmente dizem respeito a validação da conformidade das regras de negócio com o sistema, validar as funções dele. Funções geralmente possuem dados de entrada, processamento e dados de resposta. 

### Como identificar o que testar?

A abordagem empírica em testes de software, leva em consideração experiências anteriores ou interpretação de uma regra de negócio, por exemplo. Já a sistemática, leva em consideração o uso de técnicas formais de teste de software para identificar o que testar.

#### Exemplo 
RN: Apenas administradores podem registrar novas viagens
Identificar entradas:
- Credencial (Administrador = Registrar, Usuário = Não registrar e o que mais? Inválida = Não registrar e Expirada = Não registrar)
As técnicas partição ou classe de equivalência ajudam a pensar em possíveis entradas (abordagem sistemática).

![image](https://user-images.githubusercontent.com/85461130/189547547-b0838549-f392-4c16-9d63-f30be436104f.png)

Utilizando a abordagem empírica, o que vem naturalmente a cabeça são as credenciais Administrador e Usuário.

Aplicando uma técnica sistemática, é possível ampliar as possibilidades de teste.

## Como fazer testes de performance em API Rest?

Como uma API Rest responde ao elevado número de requests?
Com o teste de performance é possível simular uma grande quantidade de requisições, sem precisar recrutar usuários reais para acessarem simultâneamente. 

São testes não funcionais, contam com o já correto funcionamento da aplicação. Busca verificar como um software se comporta com uma carga de usuário definida.

Teste de performance abrenge teste de desempenho, carga, estresse e outras. 

Tempo de resposta de uma API Rest (teste de performance). 

## Como fazer testes de compatibilidade em API Rest?

Testes de compatibilidade avaliam se novas funcionalidades funcionam em conjunto com o que o sistema tem de mais antigo. 

É um teste baseado em uma das 8 características de qualidade da ISO25010. O teste de retrocompatibilidade verifica se apesar de atualizações, apps em versões antigas ainda conseguem fazer o consumo da API.

Ao fazer uma atualização na API, o ideal é executar o teste de retrocompatibilidade a fim de verificar se tudo o que já existia antes, continua funcionando para consumidores antigos.

Comparar swaggers (antigo e novo) pode ser uma estratégia de verificar a retrocompatibilidade, mas não é prático e eficiente. 

Baixar e executar o jar do swagger-diff seria uma maneira mais prática de verificar o que mudou entre diferentes versões (assinatura de método, atributos obrigatórios, deleção ou inclusão de endpoints).
https://github.com/Sayi/swagger-diff/releases/tag/v1.2.2
