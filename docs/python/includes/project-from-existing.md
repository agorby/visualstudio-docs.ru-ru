1. Запустите Visual Studio и выберите **Файл > Создать > Проект**.

1. В диалоговом окне **Создание проекта** выполните поиск по запросу "Python", выберите шаблон "На основе существующего кода Python", укажите имя и расположение проекта, а затем нажмите кнопку **ОК**.

1. В появившемся мастере задайте путь к существующему коду, фильтр для типов файлов и любые пути поиска, необходимые для проекта, а затем нажмите кнопку **Далее**. Если вы не знаете пути поиска, оставьте это поле пустым.

    ![Создание нового проекта из существующего кода, шаг 1](../media/projects-from-existing-1.png)

1. В следующем диалоговом окне выберите файл запуска для проекта и нажмите кнопку **Далее**. (При необходимости выберите среду; в противном случае оставьте значения по умолчанию.) Обратите внимание, что в диалоговом окне отображаются только файлы в корневой папке. Если нужный файл находится во вложенной папке, не указывайте файл запуска и укажите его позже в обозревателе решений (инструкции см. ниже). 

    ![Создание нового проекта из существующего кода, шаг 2](../media/projects-from-existing-2.png)

1. Выберите место, где следует сохранить файл проекта (файл `.pyproj` на диске). При необходимости можно также включить автоматическое обнаружение виртуальных сред и настроить проект для разных веб-платформ. Если вы не уверены, оставьте для этих параметров значения по умолчанию.

    ![Создание нового проекта из существующего кода, шаг 3](../media/projects-from-existing-3.png)

1.  Нажмите кнопку **Готово**, и Visual Studio создаст проект и откроет его в обозревателе решений. Если вы хотите переместить файл `.pyproj` в другое место, выберите его в обозревателе решений и щелкните **Файл > Сохранить как**. Это действие обновляет ссылки на файлы в проекте, но не перемещает файлы с кодом.

1. Чтобы указать другой файл запуска, найдите его в обозревателе решений, щелкните его правой кнопкой мыши и выберите пункт **Задать как файл запуска**.