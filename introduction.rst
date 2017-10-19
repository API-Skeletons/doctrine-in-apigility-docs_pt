Introdução
==========

O panorama das estratégias para API's crescem todos os dias. No campo do php existem
estratégias para recursos REST-only demonstrados por 
`Richardson Maturity Model Level 3 <https://martinfowler.com/articles/richardsonMaturityModel.html>`_
para API's. O apigility está na categoria Nível 3.

A API servirá dados e o Doctrine com Apigility tenta, no seu núcleo, mapear entidades Doctrine
para recursos de API comsumidos pelo Apigility. Então, um recurso habilitado para Doctrine com Apigility irá fornecer os verbos GET, POST, PUT, PATCH e DELETE de forma adequada.
Ele também permite que as relações da entidade ORM incorporem dados relacionados em um HAL (Hypertext Application Language)
Response. Isso permite que associações complexas entre entidades sejam representados no response da API.


Quando você deve usar Doctrine com Apigility?
------------------------------------------

Quando você possui um projeto usando Doctrine com associações adequadamente mapeadas e com metadados corretos entre entidades Doctrine com Apigility.
Isso proporciona um poderoso início da construção de uma API. Os metadados corretos são absolutamente essenciais para a construção de uma API
Para ajudar a projetar seu ORM `Skipper <https://skipper18.com>`_ é fortemente recomendado.

Você pode usar a Doctrine com Apigility para atender partes do seu esquema, filtrando com hydrator strategies ou você pode
servir seu esquema inteiro em uma "API de esquema aberto" onde os relacionamentos entre entidades são totalmente explorados no HAL
_embedded data.

Se você está familiarizado com os benefícios da ORM e irá usá-lo em seu projeto e você precisa de uma solução completa
O mecanismo e a estratégia dessa implementação pode ser o que você esteja procurando.