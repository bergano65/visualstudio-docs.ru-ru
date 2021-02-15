---
title: Пошаговое руководство по расширению Visual Studio для Mac
description: Узнайте, как создать простой пакет расширений для Visual Studio для Mac, добавляющий новую команду в меню "Правка".
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: 9274f86e8ade5b49b5db0c7f4773cf6fd57ea353
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876198"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Пошаговое руководство по расширению Visual Studio для Mac

Этот раздел описывает сборку [простого пакета расширения](https://github.com/mjh4/AddIns/tree/master/DateInserter). Данный пакет расширения создаст в меню правки Visual Studio для Mac новую команду, позволяющую пользователю вставлять текущую дату и время в открытый текстовый документ.

В этом примере используется Add-in Maker. Add-in Maker создает шаблон проекта и заполняет его нужными файлами для нашего пользовательского пакета расширения.

1. Для начала запустите систему Visual Studio для Mac, если она еще не открыта:

   ![Снимок экрана Visual Studio для Mac](media/extending-visual-studio-mac-addin3.png)

2. Установите _пакет расширения Add-in Maker_ с помощью диспетчера расширений. В меню Visual Studio выберите **Расширения...**:

   ![Вкладка "Диспетчер надстроек"](media/extending-visual-studio-mac-addin4.png)

3. Перейдите на вкладку "Коллекция" и введите `Addin Maker` в строку поиска в правом верхнем углу. Выберите Addin Maker в категории "Add-in Development" (Разработка надстроек) и нажмите кнопку <kbd>Установить</kbd>. Если ничего не отображается, нажмите кнопку "Обновить" и повторите поиск:

   ![Диспетчер надстроек](media/extending-visual-studio-mac-addin5.png)

4. Установив Addin Maker, вы можете приступить к созданию пакета расширения. Начнем с создания решения.

5. В диалоговом окне **Новое решение** выберите шаблон **Другие > Прочее > Общие > Xamarin Studio Addin > C#**, а на следующем экране назовите новое решение `DateInserter`:

   ![Создание решения](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio для Mac заполнит новое решение:

   ![Заполненное решение](media/extending-visual-studio-mac-addin8.png)

7. Удалите код шаблона в `Manifest.addin.xml` и замените его следующим:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Теперь требуется настроить файлы, которые в конечном счете будут обрабатывать вставку даты и времени в текстовом редакторе. Щелкните узел проекта правой кнопкой мыши и добавьте новый файл. Выберите **Общие > Пустой класс** и назовите новый файл *InsertDateHandler*:

   ![Обработчик вставки даты](media/extending-visual-studio-mac-addin9.png)

9. Давайте удалим код шаблона из `InsertDateHandler.cs` и заменим его следующим:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Позже мы расширим два этих метода-заполнителя.

10. Щелкните проект **DateInserter** правой кнопкой мыши и выберите **Добавить > Новый файл**. Выберите **Общие > Пустое перечисление**, а затем назовите новый файл *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Добавьте команду `InsertDate` в качестве нового перечисления в файл `DateInserterCommands.cs`:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. Теперь в вашем распоряжении должен быть работающий пакет расширения. Вы можете протестировать его, сохранив работу и запустив приложение. Интегрированная среда разработки запустит новый экземпляр Visual Studio для Mac с установленным новым пакетом расширения. Если вы перейдете в **меню правки**, то увидите, что Visual Studio для Mac содержит новый параметр **Insert Date** (Вставить дату), как показано на снимке экрана ниже:

    ![Команда "Insert Date" (Вставить дату)](media/extending-visual-studio-mac-addin11.png)

    Обратите внимание, что при выборе команды "Insert Date" (Вставить дату) ничего не происходит, так как текущая реализация имеет только методы-заполнители.

13. Основа для пакета расширения сформирована, пора написать код, используемый для вставки даты. Прежде всего сделайте так, чтобы **команда вставки даты** была активна только в том случае, если у пользователя открыт текстовый файл, заменив метод `Update` в `InsertDateHandler.cs` следующим кодом:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Обновите метод `Run` команды для вставки даты и времени с помощью следующего кода:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Наконец, давайте запустим пакет расширения, чтобы проверить его. В новом экземпляре Visual Studio для Mac выберите **Edit > Insert Date** (Правка > Вставить дату). Текущая дата и время вставляются в позиции курсора, как показано на снимке экрана ниже:

    ![Снимок экрана со вставкой даты](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>См. также

- [Создание первого расширения (Visual Studio в Windows)](/visualstudio/extensibility/extensibility-hello-world)