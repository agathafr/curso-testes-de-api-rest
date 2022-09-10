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
