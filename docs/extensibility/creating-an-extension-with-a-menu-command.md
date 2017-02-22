---
title: "Создание расширения с помощью команды меню | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "запись vspackage"
  - "VSPackage"
  - "учебники"
  - "пакет Visual studio"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
caps.handback.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание расширения с помощью команды меню
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать расширение с помощью команды меню, которое запускает приложение Блокнот.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание команды меню  
  
1.  Создайте проект VSIX с именем **FirstMenuCommand**. Можно найти шаблон проекта VSIX в **Новый проект** диалоговом окне под **Visual C\# и расширяемость**.  
  
2.  При открытии проекта, Добавление пользовательской команды элемента шаблона с именем **FirstCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **Добавить или создать элемент**. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C\# и расширяемость** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **FirstCommand.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр в разделе [Экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте  **средства\-расширения и обновления** окна. Вы должны увидеть **FirstMenuCommand** здесь расширения. \(Если вы откроете **расширения и обновления** в работе экземпляра Visual Studio, вы не увидите **FirstMenuCommand**\).  
  
     Теперь перейдите к **средства** меню в экспериментальном экземпляре. Вы должны увидеть **вызова FirstCommand** команды. На этом этапе он просто появляется окно сообщения с сообщением «FirstCommandPackage внутри FirstMenuCommand.FirstCommand.MenuItemCallback\(\)». Мы рассмотрим фактически запустить Блокнот из этой команды в следующем разделе.  
  
## Изменение обработчик команды меню  
 Теперь изменим обработчик команды для запуска блокнота.  
  
1.  Остановить отладку и вернуться к работе экземпляра Visual Studio. Откройте файл FirstCommand.cs и добавьте следующий оператор using:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  Найдите закрытый конструктор FirstCommand. Это где команда подключен к службе команды и указанный обработчик команды. Измените имя обработчика команды StartNotepad, следующим образом.  
  
    ```c#  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Удалите метод MenuItemCallback и добавьте метод StartNotepad, который будет просто запустить Блокнот:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Теперь попробуйте все в деле. При отладке проекта и нажмите кнопку **инструменты и вызвать FirstCommand**, вы увидите экземпляр Notepad начать работу.  
  
     Можно использовать экземпляр <xref:System.Diagnostics.Process> класса для выполнения любой исполняемый файл, а не только «Блокнот». Попытка с calc.exe, например.  
  
## Очистка экспериментальной среде  
 Если разрабатывается несколько расширений, или просто изучение результатов с разными версиями кода расширения, экспериментальной среде может перестать работать как должно. В этом случае следует запустить сценарий сброса. Он называется **Сброс экспериментального экземпляра Visual Studio 2015**, и он входит в состав пакета SDK для Visual Studio. Этот сценарий удаляет все ссылки на модули из экспериментальной среды, поэтому можно начать с нуля.  
  
 Вы можете получить на этот сценарий одним из двух способов:  
  
1.  На рабочем столе найти **Сброс экспериментального экземпляра Visual Studio 2015**.  
  
2.  В командной строке выполните следующую команду:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## Развертывание расширения  
 Теперь, когда имеется средство расширения с нужным образом, пора подумать о совместной работы с коллегами и друзьями. Это просто, поскольку они имеют установлена Visual Studio 2015. Все, что нужно сделать — отправить их в VSIX\-файл, созданный. \(Не забудьте построения в режиме выпуска\).  
  
 Для этого расширения VSIX\-файл можно найти в каталоге bin FirstMenuCommand. В частности предполагая, что при построении конфигурации выпуска, он будет выглядеть в:  
  
 **\< каталог кода \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 Чтобы установить расширение, вашего друга необходимо закрыть все открытые экземпляры Visual Studio, а затем дважды щелкните VSIX\-файл, который появляется **установщик VSIX**. Файлы копируются в **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** каталога.  
  
 Когда ваш друг обеспечит Visual Studio снова, он найти расширение FirstMenuCommand в **средства\-расширения и обновления**. Он может перейти к **расширения и обновления** удаление или отключение расширения слишком.  
  
## Дальнейшие действия  
 В этом пошаговом руководстве были показаны только небольшую часть возможностях расширения Visual Studio. Вот краткий список прочего \(довольно просто\), что можно сделать с помощью расширений Visual Studio:  
  
1.  Можно выполнять различные дополнительные действия с помощью простого меню команды:  
  
    1.  Добавьте собственный значок: [Добавление значков на команды меню](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Измените текст команды меню: [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Добавьте команду контекстного меню: [Привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Добавьте различные виды команд, меню и панели инструментов: [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)  
  
3.  Добавьте средство windows и расширять встроенные окон инструментов Visual Studio: [Расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Добавьте существующие редакторы кода IntelliSense, код предложения и другие функции: [Расширение редактора и языковые службы](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Добавьте параметры и свойства страницы и параметры пользователя для расширения: [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md) и [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)  
  
 Другие виды расширений требуют немного большей работы, таких как создание нового типа проекта \([Расширение проектов](../extensibility/extending-projects.md)\), создание нового типа редактора \([Создание пользовательские редакторы и конструкторы](../extensibility/creating-custom-editors-and-designers.md)\), или реализации расширения в изолированной оболочки: [Visual Studio изолированной оболочки](../extensibility/visual-studio-isolated-shell.md)