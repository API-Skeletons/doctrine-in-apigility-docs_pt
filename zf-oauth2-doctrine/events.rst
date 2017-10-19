Eventos
=======


Os eventos são totalmente suportados. Os valores de retorno são usados se a propagação for interrompida permitindo que você
escreva seus próprios manipuladores para qualquer método de adaptador OAuth2. Cada função que implementa
as interfaces OAuth2 podem ser atachadas e opcionalmente substituídas.


Exemplo para atachar evento
---------------------------

*Module.php onBootstrap*::

    $doctrineOAuth2Adapter = $e->getParam('application')
        ->getServiceManager()
        ->get('oauth2.doctrineadapter.default')
         ;
    $listenerAggregate = new \Application\EventSubscriber\OAuth2AggregateListener($objectManager);
    $doctrineOAuth2Adapter->getEventManager()->attachAggregate($listenerAggregate);


*Application\EventSubscriber\OAuth2AggregateListener*::

    namespace Application\EventSubscriber;

    use Zend\EventManager\Event;
    use Zend\EventManager\AbstractListenerAggregate;
    use Zend\EventManager\EventManagerInterface;

    class OAuth2AggregateListener extends AbstractListenerAggregate
    {
        protected $handlers = array();
        protected $logInAs;

        public function attach(EventManagerInterface $events)
        {
            $this->handlers[] = $events->attach('checkUserCredentials', array($this, 'checkUserCredentials'));
        }

        /**
         * Do work such as non-standard encrypted password checking
         */
        public function checkUserCredentials(Event $e)
        {
            if ($e->getParams()['username'] == 'specialUser') {
                $e->stopPropagation();

                return true;
            }
        }
    }
