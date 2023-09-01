# Управление ключевыми парами шифрования

С помощью {{ kms-name }} вы можете создавать, изменять и удалять асимметричные ключевые пары шифрования.

## Создать ключевую пару шифрования {#create}

Чтобы создать новую ключевую пару шифрования:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder), в котором будет создана ключевая пара.
  1. В списке сервисов выберите **{{ kms-name }}**.
  1. На панели слева выберите **Асимметричные ключи**.
  1. В правом верхнем углу нажмите кнопку **Создать ключ**. В открывшемся окне:
      1. Укажите имя и при необходимости описание в свободной форме.
      1. В поле **Тип** выберите **Шифрование**.
      1. В поле **Алгоритм** выберите нужный алгоритм шифрования.
      1. При необходимости включите защиту от удаления.
      1. Нажмите кнопку **Создать**.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  1. Посмотрите описание команды CLI для создания ключевой пары шифрования:

      ```bash
      yc kms asymmetric-encryption-key create --help
      ```

  1. [Получите](../../resource-manager/operations/folder/get-id.md) идентификатор каталога, в котором нужно создать ключевую пару.

  1. Создайте ключевую пару:

      ```bash
      yc kms asymmetric-encryption-key create \
        --name <имя_ключевой_пары> \
        --encryption-algorithm <алгоритм_шифрования> \
        --folder-id <идентификатор_каталога>
      ```
      
      Где:
      * `--name` — имя ключевой пары шифрования.
      * `--folder-id` — идентификатор каталога, в котором будет создана ключевая пара.
      * `--encryption-algorithm` — алгоритм шифрования. Доступные варианты:

          * `rsa-2048-enc-oaep-sha-256`
          * `rsa-3072-enc-oaep-sha-256`
          * `rsa-4096-enc-oaep-sha-256`
      
      Результат:

      ```bash
      id: abjfmo5enqlr********
      folder_id: b1gt6g8ht345********
      created_at: "2023-08-16T18:10:03Z"
      name: sample-encryption-key
      status: ACTIVE
      encryption_algorithm: RSA_2048_ENC_OAEP_SHA_256
      ```

{% endlist %}

## Изменить ключевую пару шифрования {#update}

После создания ключевой пары шифрования вы можете изменить ее имя, описание, метки, а также включить или выключить защиту от удаления.

Чтобы изменить ключевую пару шифрования:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder), в котором находится нужная ключевая пара.
  1. В списке сервисов выберите **{{ kms-name }}**.
  1. На панели слева выберите **Асимметричные ключи**.
  1. Перейдите на вкладку **Шифрование**.
  1. В строке с нужной ключевой парой нажмите значок ![image](../../_assets/horizontal-ellipsis.svg) и выберите **Изменить**. В открывшемся окне:
      1. Измените необходимые атрибуты ключевой пары.
      1. Нажмите кнопку **Сохранить**.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  1. Посмотрите описание команды CLI для изменения ключевой пары шифрования:

      ```bash
      yc kms asymmetric-encryption-key update --help
      ```

  1. [Получите](../../resource-manager/operations/folder/get-id.md) идентификатор каталога, в котором находится ключевая пара.
  
  1. {% include [get-asymmetric-encryption-key](../../_includes/kms/get-a-encryption-key.md) %}
  
  1. Измените ключевую пару:

      ```bash
      yc kms asymmetric-encryption-key update \
        --id <идентификатор_ключевой_пары> \
        --new-name <новое_имя_ключевой_пары> \
        --deletion-protection
      ```

      Где:
      * `--id` — идентификатор ключевой пары шифрования.
      * `--new-name` — новое имя ключевой пары.
      * `--deletion-protection` — флаг включения защиты от удаления. Чтобы отключить защиту ключевой пары от удаления, используйте флаг `--no-deletion-protection`.

      Результат:

      ```bash
      id: abjfmo5enqlr********
      folder_id: b1gt6g8ht345********
      created_at: "2023-08-16T18:10:03Z"
      name: new-encryption-key
      status: ACTIVE
      encryption_algorithm: RSA_2048_ENC_OAEP_SHA_256
      deletion_protection: true
      ```

      Команда изменила имя ключевой пары шифрования и включила защиту от удаления.

{% endlist %}

## Удалить ключевую пару шифрования {#delete}

Чтобы удалить ключевую пару шифрования:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder), в котором находится нужная ключевая пара.
  1. В списке сервисов выберите **{{ kms-name }}**.
  1. На панели слева выберите **Асимметричные ключи**.
  1. Перейдите на вкладку **Шифрование**.
  1. В строке с нужной ключевой парой нажмите значок ![image](../../_assets/horizontal-ellipsis.svg) и выберите **Удалить**.
  1. Подтвердите удаление.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  1. Посмотрите описание команды CLI для удаления ключевой пары шифрования:

      ```bash
      yc kms asymmetric-encryption-key delete --help
      ```

  1. [Получите](../../resource-manager/operations/folder/get-id.md) идентификатор каталога, в котором находится ключевая пара.
  
  1. {% include [get-asymmetric-encryption-key](../../_includes/kms/get-a-encryption-key.md) %}
  
  1. Удалите ключевую пару, указав ее идентификатор:

      ```bash
      yc kms asymmetric-encryption-key delete \
        --id <идентификатор_ключевой_пары>
      ```

      Результат:

      ```bash
      id: abjfmo5enqlr********
      folder_id: b1gt6g8ht345********
      created_at: "2023-08-16T18:10:03Z"
      name: new-encryption-key
      encryption_algorithm: RSA_2048_ENC_OAEP_SHA_256
      ```

{% endlist %}