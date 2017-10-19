Diagrama de Entidade Relacionamento
===================================

.. image:: https://raw.githubusercontent.com/API-Skeletons/zf-oauth2-doctrine/master/media/oauth2-doctrine-erd.png

Entity Relationship Diagram created with `Skipper <https://skipper18.com>`_

The ERD module is located at
`media/OAuth2-orm.module.xml <https://github.com/API-Skeletons/zf-oauth2-doctrine/blob/master/media/OAuth2-orm.module.xml>`_
and is intended to be embedded in the ERD for your project.


Relações
--------

A entidade do usuário é fornecida pelo seu aplicativo e uma junção dinâmica é feita em tempo de execução quando os metadados são coletados pelo Doctrine. Existe uma união dinâmica com Client, AuthorizationCode, AccessToken and RefreshToken.

A entidade central OAuth2 é o Client. Existe uma associação dinâmica da entidade Client à entidade de usuário configurada. Para cada aplicativo de um Usuário, haverá uma entrada de Client. O Usuário referenciado a partir de um Client é o Usuário que possui esse Client.

A entidade AuthorizationCode é usada quando um Usuário se conecta a partir de um aplicativo usando OAuth2. A referência à entidade de usuário da entidade AuthorizationCode é para o Usuário que está tentando fazer logon no Client referenciado pela entidade AuthorizationCode. O mesmo acontece com as entidades AccessToken e RefreshToken.

As entidades Scope tem a relação de muitos para muitos para Client, AuthorizationCode, AccessToken e RefreshToken. Scopes determina quais permissões um cliente tem na API.

Existe um relacionamento de um para um do Client para o PublicKey. Isso ocorre porque o lado de criptografia do OAuth2 é menos comum e encapsulam os campos de criptografia na entidade PublicKey. As entidades JWT e JTI oferecem suporte total e seu uso na criptografia ficando de fora do escopo desta documentação.


Namespaces das tabelas do banco de dados
----------------------------------------

Todas as tabelas OAuth2 são sufixadas com _OAuth2, como Client_OAuth2. Você pode alterá-los :ref:`override`.
Recomenda-se que seus nomes de tabela de banco de dados correspondam aos nomes de sua entidade para fornecer nomes canônicos em sua aplicação.
Veja também `bushbaby/zf-oauth2-doctrine-mutatetablenames <https://github.com/basz/zf-oauth2-doctrine-mutatetablenames>`_.
