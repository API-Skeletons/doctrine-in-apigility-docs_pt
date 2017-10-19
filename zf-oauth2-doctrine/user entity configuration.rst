Configuração de entidade de usuário
===================================

Este repositório fornece todas as entidades que você precisa para implementar OAuth2
exceto a entidade de usuário. A razão é para que a entidade do usuário possa ser
desacoplado do repositório do OAuth2 Doctrine em vez disso para ser vinculado
dinamicamente em tempo de execução. Isso permite, entre outros benefícios, a capacidade
para criar um ERD sem modificar o módulo 'OAuth2-orm.module.xml`.

A entidade do usuário deve implementar ``ZF\OAuth2\Doctrine\Entity\UserInterface``

A entidade de usuário para o teste de unidade para este módulo é um bom modelo para começar a partir de:
`https://github.com/api-skeletons/zf-oauth2-doctrine/blob/master/test/asset/module/Doctrine/src/Entity/User.php <https://github.com/api-skeletons/zf-oauth2-doctrine/blob/master/test/asset/module/Doctrine/src/Entity/User.php>`_

