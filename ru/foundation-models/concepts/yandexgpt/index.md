# Обзор {{ yagpt-full-name }}

{{ yagpt-full-name }} позволит вам быстро создавать текстовый контент: генерировать описание товаров, статьи, новости, информационные рассылки, посты для блога и многое другое. Качество ответа нейросети напрямую зависит от точности переданной инструкции: чем точнее вы опишете свой запрос, тем выше вероятность получить ожидаемый результат. Примеры инструкций и запросов собраны в [библиотеке промтов {{ yagpt-full-name }}](../../prompts/yandexgpt/index.md).

Модель понимает промты на русском и английском языках, но в первую очередь предназначена для работы с русскоязычными текстами. Кроме текстового описания в промтах необходимо указывать специальный параметр _температура_, который определяет вариативность ответа модели: чем выше значение температуры, тем более непредсказуемым будет результат выполнения запроса.

Для работы с {{ yagpt-full-name }} в {{ yandex-cloud }} доступны два интерфейса. Вы можете отправлять запросы в [{{ foundation-models-name }} Playground]({{ link-console-main }}/link/foundation-models/) или интегрировать модель в свои приложения с помощью API. Для интеграции доступны интерфейсы [REST](../../text-generation/api-ref/index.md) и [gRPC](../../text-generation/api-ref/grpc/index.md).

{{ foundation-models-name }} Playground подойдет для знакомства и тестирования: в нем вы можете отправлять синхронные запросы к моделям {{ yagpt-full-name }}. При этом на выбор доступны два формата общения с моделью:

* **Промт-режим** позволит вам отправить в модель подготовленный промт и получить результат. При этом каждый новый вопрос модель воспринимает как самостоятельное задание и не сохраняет контекст предыдущего обращения. В этом формате в консоли управления на выбор доступны модели краткого пересказа, {{ gpt-lite}} и {{ gpt-pro }}.

* Режим **Чат** позволит вам переписываться с моделью, уточняя задания и дополняя предыдущие реплики. Контекст общения передается в каждом сообщении и сохраняется в течение сессии, пока вы явно не начнете новую сессию. В режиме чата доступна модель {{ gpt-pro }}.

И [промт-сообщения](../../operations/yandexgpt/create-prompt.md), и [сообщения в режиме чат](../../operations/yandexgpt/create-chat.md) также доступны при работе через API. Также вы можете использовать API для работы с моделями в [асинхронном режиме](../../operations/yandexgpt/async-request.md).

Подробнее о моделях {{ yagpt-full-name }} см. в разделе [{#T}](models.md).