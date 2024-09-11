# MTK SP Flash Tool Readback feature file generator

Phones on MTK processors can be fully backed up woth the use of SP Flash Tool utility. This backup can be used for restoring phone's functionality after major problews with its firmware, including full dead brick (wrong flash of boot.img, preloader.bin) that does not react on buttons no logo, no charging sign. The NVRAM and NVDATA partitions that contain IMEI numbers, reuired for the phone operation, can be backed up.

In order to make SP Flash Tool functional a phone must have an unlocked bootloader. Not all smartphone vendors allow to unlock bootloader. The butloader has to be unlocked when the phone is functioning normally.

The script takes the data on partition's offset and partition length from the Scatter.txt file, which is unique for each smarphone model. The Scatter file can be obtained from the official firmware for the smartphone.

Take the output of the script and paste it into the ```readback_ui_bak.xml``` file located in the the SP flash tool directory.

Note the preloader readback adress should be added manually, since it is located in other part of the phone's NAND flash.

The  ```readback_ui_bak.xml``` file is created automatically by the SP flash tool on any edit on the Readback tab. Ensure your file follows the structure. Verify the backup folder path leads to an existing folder on yur disk.

```
<?xml version="1.0" encoding="UTF-8" ?>
<flashtool-config version="2.0">
    <general>
        <chip-name>MT6765</chip-name>
        <storage-type>EMMC</storage-type>
    </general>
    <commands>
        <readback>
            <physical-readback is-physical-readback="false" />
            <readback-list>
                <readback-rom-item readback-index="0" readback-enable="true" readback-flag="NUTL_READ_PAGE_ONLY" start-address="0x0000000000000000" readback-length="0x00040000" addr-flag="NUTL_ADDR_LOGICAL" part-id="32">D:\backup\preloader</readback-rom-item>
                <readback-rom-item readback-index="1" readback-enable="true" readback-flag="NUTL_READ_PAGE_ONLY" start-address="0x0000000000000000" readback-length="0x00008000" addr-flag="NUTL_ADDR_LOGICAL" part-id="34">D:\backup\nvram</readback-rom-item>
            </readback-list>
        </readback>
    </commands>
</flashtool-config>

```

## MTK SP Flash Tool генератор файла функции Readback

Телефоны на процессорах MTK можно полностью сохранить с помощью утилиты SP Flash Tool. Этот резервный файл можно использовать для восстановления работоспособности телефона после серьезных проблем с его прошивкой, включая полный "кирпич" (ошибочная прошивка boot.img, preloader.bin), при котором устройство не реагирует на кнопки, нет логотипа, нет признаков зарядки. Разделы NVRAM и NVDATA, которые содержат IMEI-номера, необходимые для работы телефона, также можно сохранить.

Чтобы SP Flash Tool мог функционировать, телефон должен иметь разблокированный загрузчик. Не все производители смартфонов позволяют разблокировать загрузчик. Загрузчик должен быть разблокирован, пока телефон находится в рабочем состоянии.

Скрипт берет данные о смещении разделов и длине разделов из файла Scatter.txt, который уникален для каждой модели смартфона. Файл Scatter можно получить из официальной прошивки для смартфона.

Выведите результат работы скрипта и вставьте его в файл ```readback_ui_bak.xml```, расположенный в директории SP Flash Tool.

Обратите внимание, что адрес readback раздела preloader нужно добавить вручную, так как он расположен в другой части NAND-флеш телефона.

Файл ```readback_ui_bak.xml``` создается автоматически SP Flash Tool при любом редактировании вкладки Readback. Убедитесь, что ваша версия файла соответствует структуре. Проверьте, что путь к папке резервного копирования ведет к существующей папке на вашем диске.
