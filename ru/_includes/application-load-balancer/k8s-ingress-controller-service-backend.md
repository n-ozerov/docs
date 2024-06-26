* `name` (`string`, обязательное)

  Имя сервиса {{ k8s }}.

* `port` (`ServiceBackendPort`, обязательное)

  Порт сервиса, к которому будет обращаться `Ingress`.

  Поле предназначено для работы Ingress-контроллера и не соответствует ни одному из полей ресурсов {{ alb-name }}.

  * `name` (`string`)

    Имя порта сервиса.

    Имя должно совпадать с одним из имен портов, указанных в полях `spec.ports.name` ресурса `Service`. Подробнее см. в [спецификации ресурса](../../application-load-balancer/k8s-ref/service-for-ingress.md).

    Для порта сервиса должно быть указано либо имя, либо номер (`number`), но не оба одновременно.

  * `number` (`int32`)

    Номер порта сервиса.

    Номер должен совпадать с одним из номеров портов, указанных в полях `spec.ports.port` ресурса `Service`. Подробнее см. в [спецификации ресурса](../../application-load-balancer/k8s-ref/service-for-ingress.md).

    Для порта сервиса должен быть указан либо номер, либо имя (`name`), но не оба одновременно.