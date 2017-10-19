Configuração da aplicação
=========================


Instalação
----------

A instalação deste módulo usa composer. Para documentação de referência consulte `getcomposer.org <http://getcomposer.org/>`_::

``composer require api-skeletons/zf-oauth2-doctrine "^1.0"``

Adicione este módulo à configuração de sua aplicação::

    'modules' => [
       ...
       'ZF\OAuth2\Doctrine',
    ],

Configuração Global
--------------------

Copy ``config/oauth2.doctrine-orm.global.php.dist`` to your autoload directory and
rename to ``oauth2.doctrine-orm.global.php`` This config has multiple sections for multiple
adapters.  Out of the box this module provides a `default` adapter.  You will need to edit this file with
at least your User entity, which is not provided.


Configuração zfcampus/zf-mvc-auth
----------------------------------

By default this module includes a `oauth2.doctrineadapter.default` adapter.
The adapter is used to create storage from services.
Add this configuration to your `config/autoload/zf-mvc-auth-oauth2-override.global.php`::

    'zf-mvc-auth' => array(
        'authentication' => array(
            'adapters' => array(
                'oauth2_doctrine' => array(
                    'adapter' => 'ZF\\MvcAuth\\Authentication\\OAuth2Adapter',
                    'storage' => array(
                        'storage' => 'oauth2.doctrineadapter.default',
                        'route' => '/oauth',
                    ),
                ),
            ),
        ),
    ),


zfcampus/zf-oauth2 Configuration
--------------------------------

Add the default storage adapter to the zf-oauth default storage.
``zfcampus/zf-oauth2`` provides an ``oauth2.local.php`` file.  This
repository's recommendation is to create a new ``config/autoload/oauth2.global.php``
file and set the following configuration as well as any
`OAuth2 server settings <https://github.com/bshaffer/oauth2-server-php/blob/develop/src/OAuth2/Server.php#L109>`_ e.g. ``allow_implicit``::

    'zf-oauth2' => array(
        'storage' => 'oauth2.doctrineadapter.default',
