Снимок диска содержит только те данные, которые были записаны на диск в момент создания снимка. Если диск подключен к работающей виртуальной машине, то кеш приложений и операционной системы не попадет в снимок.

Чтобы обеспечить целостность данных снимка:

{% list tabs %}

- Linux

  1. Остановите все операции записи на диск в приложениях.

  1. Запишите кэш операционной системы на диск:

      ```bash
      sync
      ```

  1. Заморозьте файловую систему:

      ```bash
      sudo fsfreeze --freeze <точка_монтирования>
      ```
      Где `--freeze` — параметр для заморозки файловой системы. Вместо `<точка_монтирования>` укажите каталог, к которому подключена файловая система. Например: `/mnt/vdc2`.

  1. Создайте снимок по инструкции [ниже](#create).

  1. Разморозьте файловую систему:

      ```bash
      sudo fsfreeze --unfreeze <точка_монтирования>
      ```
      Где `--unfreeze` — параметр для разморозки файловой системы. Вместо `<точка_монтирования>` укажите каталог, к которому подключена файловая система. Например: `/mnt/vdc2`.

- Другие ОС

  1. Остановите виртуальную машину (см. раздел [{#T}](../../compute/operations/vm-control/vm-stop-and-start.md#stop)).
  1. Дождитесь, когда статус машины изменится на `STOPPED`.

{% endlist %}