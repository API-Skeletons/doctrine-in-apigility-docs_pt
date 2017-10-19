zf-doctrine-apigility Integration
=================================

Validar recursos para zf-apigility-doctrine
-------------------------------------------

Para validar a sessão com ``Query Create Filters`` e ``Query Providers`` implement
``ZF\OAuth2\Doctrine\OAuth2ServerInterface`` e use ``ZF\OAuth2\Doctrine\OAuth2ServerTrait``.
Em seguida faça uma chamada ``$result = $this->validateOAuth2($scope);`` na função de filtro.
