---
title: "Создание расширения с помощью команды меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e9f72764d8fc87a9605f3bde20b7b2b93f44f39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню
В этом пошаговом руководстве показано, как создать расширение с помощью команды меню, которое запускает приложение Блокнот.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Создание команды меню  
  
1.  Создайте проект VSIX с именем **FirstMenuCommand**. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта, Добавление пользовательской команды элемента шаблона с именем **FirstCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **FirstCommand.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте **средства / расширения и обновления** окна. Вы увидите **FirstMenuCommand** здесь расширения. (Если вы откроете **расширения и обновления** в работе экземпляра Visual Studio, вы не увидите **FirstMenuCommand**).  
  
     Теперь перейдите к **средства** меню в экспериментальном экземпляре. Вы увидите **FirstCommand вызова** команды. На этом этапе он просто появится окно сообщения об ошибке «FirstCommandPackage внутри FirstMenuCommand.FirstCommand.MenuItemCallback()». Мы рассмотрим, как фактически запустить Блокнот из эту команду в следующем разделе.  
  
## <a name="changing-the-menu-command-handler"></a>Изменение обработчика команд меню  
 Теперь давайте обновить обработчик команд для запуска блокнота.  
  
1.  Остановить отладку и вернуться к работе экземпляра Visual Studio. Откройте файл FirstCommand.cs и добавьте следующий код с помощью инструкции:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Найти закрытый конструктор FirstCommand. Это где команда подключен к службе команды и указанный обработчик команд. Измените имя обработчика команд StartNotepad, следующим образом.  
  
    ```csharp  
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
  
3.  Удалите метод MenuItemCallback и добавьте метод StartNotepad, который будет просто запустите Блокнот:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Теперь попробуйте все в деле. Запуск отладки проекта при нажатии **Сервис / вызвать FirstCommand**, вы увидите экземпляр блокнота начать работу.  
  
     Можно использовать экземпляр <xref:System.Diagnostics.Process> для выполнения любой исполняемый файл, а не только «Блокнот». Попробуйте сделать это с calc.exe, например.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Очистка экспериментальной среды  
 Если вы разрабатываете несколько расширений, просто изучение результатов с разными версиями код модуля, экспериментальный среды могут перестать работать того, который следует. В этом случае следует запустить сценарий сброса. Он вызывается **Сброс экспериментального экземпляра Visual Studio 2015**, и он входит в состав пакета SDK для Visual Studio. Этот сценарий удаляет все ссылки на расширения из экспериментальной среды, чтобы вы могли начать с нуля.  
  
 Чтобы узнать этот сценарий в одном из двух способов:  
  
1.  На рабочем столе найти **Сброс экспериментального экземпляра Visual Studio 2015**.  
  
2.  В командной строке выполните следующую команду:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Развертывание расширения  
 Теперь, когда средство расширения под управлением нужным образом, пришло время подумать о совместной работы с коллегами и друзьями. Это просто, при условии, что они имеют установленной Visual Studio 2015. Вы должны делать достаточно отправить их в VSIX-файл, созданных вами. (Необходимо построить его в режиме выпуска).  
  
 Для этого расширения VSIX-файл можно найти в каталоге bin FirstMenuCommand. В частности при условии, что вы создали конфигурации выпуска, он будет в:  
  
 **\<каталог кода > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Чтобы установить расширение, друга необходимо закрыть все открытые экземпляры Visual Studio, а затем дважды щелкните VSIX-файл, который можно открыть **установщик VSIX**. Файлы копируются в **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** каталога.  
  
 Когда друг снова открыть Visual Studio, он сможете найти расширение FirstMenuCommand в **средства / расширения и обновления**. Он может перейти к **расширения и обновления** удаление или отключение расширения слишком.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 В данном пошаговом руководстве было показано только небольшую часть возможности расширения Visual Studio. Вот короткий список прочего (достаточно просто), которые можно выполнить с помощью расширений Visual Studio:  
  
1.  Можно сделать многими другими возможностями с помощью простого меню команды.  
  
    1.  Добавить собственные значок: [добавление значков команды меню](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Изменить текст команды меню: [изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Добавить контекстное меню для команды: [привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Добавить различные команды, меню и панели инструментов: [расширение меню и команд](../extensibility/extending-menus-and-commands.md)  
  
3.  Добавлять окна инструментов и расширения встроенных окна инструментов Visual Studio: [расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Добавьте IntelliSense, предложения кода и другие функции для существующих редакторов кода: [расширение редактора и языковые службы](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Добавить параметры и свойства страницы и параметры пользователя для модуля: [расширение свойств и в окне свойств](../extensibility/extending-properties-and-the-property-window.md) и [расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)  
  
 Другие виды расширений, требуют небольшую дополнительную работу, например для создания нового типа проекта ([расширение проектов](../extensibility/extending-projects.md)), создания нового типа редактора ([создания пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)), или реализация модуля в изолированной оболочки: [изолированной оболочки Visual Studio](../extensibility/visual-studio-isolated-shell.md)