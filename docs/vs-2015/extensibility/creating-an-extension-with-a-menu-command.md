---
title: Создание расширения с помощью команды меню | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572891"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать расширение с помощью команды меню, запускающей Блокнот.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Создание команды меню  
  
1. Создайте проект VSIX с именем **фирстменукомманд**. Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Visual C#/Extensibility (расширяемость**).  
  
2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **фирсткомманд**. В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел **Visual C#/Extensibility** и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на **FirstCommand.CS**.  
  
3. Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения об экспериментальном экземпляре см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4. В экспериментальном экземпляре откройте окно  **Сервис/расширения и обновления** . Здесь вы увидите расширение **фирстменукомманд** . (Если вы открыли **расширения и обновления** в рабочем экземпляре Visual Studio, вы не увидите **фирстменукомманд**).  
  
     Теперь перейдите в меню **Сервис** в экспериментальном экземпляре. Вы должны увидеть команду **Invoke фирсткомманд** . На этом этапе просто выводится окно сообщения «Фирсткоммандпаккаже in Фирстменукомманд. Фирсткомманд. Менуитемкаллбакк ()». Мы посмотрим, как запустить блокнот из этой команды в следующем разделе.  
  
## <a name="changing-the-menu-command-handler"></a>Изменение обработчика команд меню  
 Теперь выполним обновление обработчика команд для запуска Блокнота.  
  
1. Завершите отладку и вернитесь к рабочему экземпляру Visual Studio. Откройте файл FirstCommand.cs и добавьте следующую инструкцию using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Найдите закрытый конструктор Фирсткомманд. Именно в этом случае команда подключена к службе команд, и указан обработчик команд. Измените имя обработчика команды на Стартнотепад следующим образом:  
  
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
  
3. Удалите метод Менуитемкаллбакк и добавьте метод Стартнотепад, который будет просто запускать Блокнот:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. Теперь попробуйте. После начала отладки проекта и нажатия кнопки **Сервис/Invoke фирсткомманд**должен появиться экземпляр блокнота.  
  
     Экземпляр класса можно использовать <xref:System.Diagnostics.Process> для запуска любого исполняемого файла, а не только блокнота. Попробуйте использовать его с calc.exe, например.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Очистка экспериментальной среды  
 Если вы разрабатываете несколько расширений или просто изучаете результаты с разными версиями кода расширения, экспериментальная среда может перемешать работать. В этом случае следует запустить скрипт сброса. Он называется **сбросом экспериментального экземпляра Visual studio 2015**и поставляется в составе пакета SDK для Visual Studio. Этот сценарий удаляет все ссылки на расширения из экспериментальной среды, что позволяет начать с нуля.  
  
 Этот скрипт можно получить одним из двух способов:  
  
1. На рабочем столе найдите **параметр сбросить экспериментальный экземпляр Visual Studio 2015**.  
  
2. Выполните следующую команду в командной строке:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Развертывание расширения  
 Теперь, когда расширение инструментов работает так, как вам нужно, вы научитесь поделиться им с вашими друзьями и коллегами. Это просто, если на них установлен Visual Studio 2015. Все, что нужно сделать, — это отправить им созданный VSIX-файл. (Не забудьте выполнить сборку в режиме выпуска.)  
  
 VSIX файл для этого расширения можно найти в каталоге bin Фирстменукомманд. В частности, если вы создали конфигурацию выпуска, она будет находиться в следующих статьях:  
  
 **\<code directory>\Фирстменукомманд\фирстменукомманд\бин\релеасе\ Фирстменукомманд. VSIX**  
  
 Чтобы установить расширение, вашему другу нужно закрыть все открытые экземпляры Visual Studio, а затем дважды щелкнуть VSIX-файл, который открывает **установщик VSIX**. Файлы копируются в каталог **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** .  
  
 Когда ваш друг снова выполнит Visual Studio, он найдет расширение Фирстменукомманд в **меню Сервис/расширения и обновления**. Он также может обратиться к **расширениям и обновлениям** , чтобы удалить или отключить расширение.  
  
## <a name="next-steps"></a>Next Steps  
 В этом пошаговом руководстве показана только небольшая часть возможностей расширения Visual Studio. Ниже приведен краткий список других (достаточно простых) действий, которые можно выполнять с расширениями Visual Studio:  
  
1. С помощью простой команды меню можно выполнять многие другие задачи:  
  
   1. Добавьте собственный значок: [Добавление значков к командам меню](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Изменение текста команды меню: [изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Добавить в команду Ярлык меню: [Привязка сочетаний клавиш к](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) пунктам меню  
  
2. Добавление различных типов команд, меню и панелей инструментов: [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)  
  
3. Добавление окон инструментов и расширение встроенных окон инструментов Visual Studio: [расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Добавление IntelliSense, предложений кода и других функций в существующие редакторы кода: [расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Добавьте параметры и страницы свойств и параметры пользователя в расширение: [расширение свойств и окно свойств](../extensibility/extending-properties-and-the-property-window.md) , а также [расширение параметров пользователя и параметров](../extensibility/extending-user-settings-and-options.md) .  
  
   Для других типов расширений требуется немного больше работы, например создание нового типа проекта ([расширение проектов](../extensibility/extending-projects.md)), создание нового типа редактора ([Создание пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)) или реализация расширения в изолированной оболочке: [изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)
