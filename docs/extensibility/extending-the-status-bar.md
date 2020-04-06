---
title: Продление адвокатской контора «Статус» (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711542"
---
# <a name="extend-the-status-bar"></a>Расширить планку состояния
Для отображения информации можно использовать строку состояния Visual Studio в нижней части IDE.

 При расширении панели статуса можно отображать информацию и uI в четырех регионах: область обратной связи, планка прогресса, область анимации и область конструктора. Область обратной связи позволяет отображать текст и выделять отображаемый текст. Панель прогресса показывает постепенный прогресс для коротких операций, таких как сохранение файла. Область анимации отображает непрерывно зацикленную анимацию для длительных операций или операций неопределенной длины, например, для создания нескольких проектов в решении. Область конструктора показывает номер строки и столбца расположения курсора.

 Вы можете получить панель статуса с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> (от службы). <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Кроме того, любой объект, расположенный на оконной раме, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> может зарегистрироваться в качестве объекта клиента панели статуса путем реализации интерфейса. Всякий раз, когда окно активируется, Visual Studio запрашивает `IVsStatusbarUser` объект, расположенный на этом окне для интерфейса. Если найдено, он <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> вызывает метод на возвращенном интерфейсе и объект может обновить панель статуса из этого метода. Окна документов, например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> могут использовать метод для обновления информации в регионе конструктора, когда они становятся активными.

 Следующие процедуры предполагают, что вы понимаете, как создать проект VSIX и добавляете пользовательскую команду меню. Для получения информации [см. Создать расширение с командой меню.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="modify-the-status-bar"></a>Изменение панели статусов
 Эта процедура показывает, как установить и получить текст, отобразить статический текст и выделить отображаемый текст в области обратной связи в области статуса бар.

### <a name="read-and-write-to-the-status-bar"></a>Читать и писать в бар статуса

1. Создайте проект VSIX под названием **TestStatusBarExtension** и добавьте команду меню под названием **TestStatusBarCommand.**

2. В *TestStatusBarCommand.cs*заменить код метода обработчика команд ( )`MenuItemCallback`на следующее:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Составить код и начать отладку.

4. Откройте меню **Tools** в экспериментальном экземпляре Visual Studio. Нажмите кнопку **Invoke TestStatusBarCommand.**

     Вы должны видеть, что текст в статусе бар теперь читает **Мы только что написал в статус бар.** и поле сообщений, которое появляется, имеет тот же текст.

### <a name="update-the-progress-bar"></a>Обновление панели прогресса

1. В этой процедуре мы покажем, как инициализировать и обновить планку прогресса.

2. Откройте *TestStatusBarCommand.cs* файл `MenuItemCallback` и замените метод следующим кодом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Составить код и начать отладку.

4. Откройте меню **Tools** в экспериментальном экземпляре Visual Studio. Нажмите кнопку **Invoke TestStatusBarCommand.**

     Вы должны видеть, что текст в панели статуса теперь читает **Написание в бар прогресса.** Вы также должны видеть, что панель прогресса обновляется каждую секунду в течение 20 секунд. После этого бар статуса и панель прогресса очищаются.

### <a name="display-an-animation"></a>Отображение анимации

1. В панели состояния отображается анимация циклов, которая указывает либо на длительную операцию (например, создание нескольких проектов в решении). Если вы не видите эту анимацию, убедитесь, что у вас есть правильные параметры**параметры** **инструментов:** > 

     Перейдите на**вкладку** **Tools** > **Options** > General и отрегулируйте автоматически настроить **визуальный опыт на основе производительности клиента.** Затем проверьте суб-вариант **Включить богатый клиент визуальный опыт.** Теперь вы должны иметь возможность видеть анимацию при построении проекта в экспериментальном экземпляре Visual Studio.

     В этой процедуре мы отображаем стандартную анимацию Visual Studio, которая представляет собой построение проекта или решения.

2. Откройте *TestStatusBarCommand.cs* файл `MenuItemCallback` и замените метод следующим кодом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Составить код и начать отладку.

4. Откройте меню **Tools** в экспериментальном экземпляре Visual Studio и нажмите **Наймите Invoke TestStatusBarCommand.**

     Когда вы видите поле сообщений, вы также должны увидеть анимацию в панели статуса в крайнем правом. При отклонении окна сообщений анимация исчезает.
