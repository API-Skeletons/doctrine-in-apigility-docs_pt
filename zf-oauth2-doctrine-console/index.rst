OAuth2 Adapter Console Management
=================================


`api-skeletons/zf-oauth2-doctrine-console <https://github.com/API-Skeletons/zf-oauth2-doctrine-console>`_


Sobre
-----

Este repositório fornece rotas de console para gerenciar um servidor OAuth2 sem dor de cabeça.


Instalação
----------

A instalação deste módulo usa composer. Para documentação de referência consulte `getcomposer.org <http://getcomposer.org/>`_::

    composer require api-skeletons/zf-oauth2-doctrine-console "*"

Adicione este módulo à configuração de sua aplicação::

    'modules' => array(
       ...
       'ZF\OAuth2\Doctrine\Console',
    ),


Console Routes
--------------

* ``oauth2:client:create`` Crie um novo cliente com ou sem um usuário.

* ``oauth2:client:update`` Atualize um cliente.

* ``oauth2:client:delete`` Excluir um cliente.

* ``oauth2:client:list`` Listar todos os clientes.

* ``oauth2:scope:create`` Criar um escopo.

* ``oauth2:scope:update`` Atualize um escopo.

* ``oauth2:scope:delete`` Excluir um escopo.

* ``oauth2:scope:list`` Liste todos os escopos.

* ``oauth2:public-key:create`` Crie o registro de chave public/private para o cliente fornecido.
    Esses dados são usados para assinar tokens de acesso JWT. Cada cliente pode ter apenas um par de chaves.

* ``oauth2:public-key:delete`` Remova a chave pública do par de chaves de um cliente.

* ``oauth2:jwt:create`` Crie um novo JWT para um determinado cliente. Este JWT será usado por um
   conexão oauth2 solicitando um grant_type para ``urn:ietf:params:oauth:grant-type:jwt-bearer``.
  A criação do JWT coloca a chave pública do pedido de conexão oauth2 nas tabelas OAuth2.

* ``oauth2:jwt:delete`` Excluir im JWT.

* ``oauth2:jwt:list`` Liste todos os JWT.

Para o lado de conexão do JWT, `zf-oauth2-client <https://github.com/API-Skeletons/zf-oauth2-client>`_
que fornece uma ferramenta de linha de comando para gerar uma solicitação JWT.
Veja também `jwt-bearer <http://bshaffer.github.io/oauth2-server-php-docs/grant-types/jwt-bearer>`_
