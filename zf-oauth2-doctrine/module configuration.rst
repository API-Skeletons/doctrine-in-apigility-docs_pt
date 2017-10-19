Configuração do módulo
======================


Usando Entidades Padronizadas
-----------------------------

Os detalhes para criar seu banco de dados com as entidades incluídas estão fora do escopo deste projeto.
Geralmente isso é feito através de `doctrine/doctrine-orm-module <https://github.com/doctrine/DoctrineORMModule>`_
com ``php public/index.php orm:schema-tool:create``

Por padrão, este módulo usa as entidades fornecidas, mas você pode usar o adaptador com seus próprios
(e mapeá-los na seção de configuração de mapeamento) perceba que existe uma configuração que usa esta funcionalidade::

    'zf-oauth2-doctrine' => [
        'default' => [
            'enable_default_entities' => true,


Personalizando o mapeamento de muitos para um (n <= 1)
------------------------------------------------------

If you need to customize the call to mapManyToOne, which creates the dynamic joins to the User
entity from the default entites, you may add any parameters to the

Se você precisa personalizar usando mapManyToOne, que cria as assossiações dinâmicas para UserEntity padrão,
você pode adicionar estes parametros ao elemento ``['dynamic_mapping']['default_entity']['additional_mapping_data']``. 

Um exemplo para um
Entidade de usuário com uma chave primária de user_id que não está em conformidade com a estratégia de nomeação de metadados
é adicionado a cada entidade::

    'refresh_token_entity' => [
        'entity' => 'ZF\OAuth2\Doctrine\Entity\RefreshToken',
        'field' => 'refreshToken',
        'additional_mapping_data' => [
            'joinColumns' => [
                [
                    'name' => 'user_id',
                    'referencedColumnName' => 'user_id',
                ],
            ],
        ],
    ],


Campo de identidade na entidade de usuário
------------------------------------------

or padrão, este adaptador Doctrine recupera o usuário pelo `username` no campo configurado
na entidade de Usuário. Se você precisar usar um ou vários campos diferentes, você pode fazê-lo através do elemento
``auth_identity_fields``. Por exemplo, o ZfcUser permite aos usuários autenticar por campos de nome de usuário e / ou email.

Um exemplo para combinar ZfcUser ``auth_identity_fields`` a configuração::

    'zf-oauth2-doctrine' => [
        'default' => [
            'auth_identity_fields' => ['username', 'email'],
