---
title: Подписка на событие Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699686"
---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом шаге объясняется, как создать окно инструментов, реагируя на события в таблице запущенных документов (RDT). Окно инструмента размещает пользовательский <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>элемент управления, который реализуется. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> соединяет интерфейс с событиями.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Подписка на мероприятия RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Создание расширения с окном инструмента

1. Создайте проект под названием **RDTExplorer** с помощью шаблона VSIX и добавьте шаблон пользовательского окна инструмента под названием **RDTExplorerWindow.**

     Для получения дополнительной информации о создании расширения с окном инструмента [см.](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>Подписаться на мероприятия RDT

1. Откройте файл RDTExplorerWindowControl.xaml и `button1`удалите названную кнопку. Добавьте <xref:System.Windows.Forms.ListBox> элемент управления и примите имя по умолчанию. Элемент Grid должен выглядеть следующим образом:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Откройте RDTExplorerWindow.cs файл в представлении кода. Добавьте следующие директивы с помощью к началу файла.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Измените `RDTExplorerWindow` класс таким образом, чтобы, помимо вытекающих <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> из <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> класса, он реализовывал интерфейс.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Реализация интерфейса. Поместите курсор на имя IVsRunningDocTableEvents. Вы должны увидеть лампочку в левом крае. Нажмите на стрелку Down справа от лампочки и выберите **интерфейс Implement.**

5. В каждом методе в интерфейсе замените линию `throw new NotImplementedException();` на это:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Добавьте поле cookie в класс RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     В этом содержится файл <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> cookie, который возвращается методом.

7. Переопределить метод инициализации RDTExplorer Window для регистрации событий RDT. Вы всегда должны получать услуги в методе инициализации () ToolWindowPane, а не в конструкторе.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Служба <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> называется для <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> получения интерфейса. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> соединяет события RDT с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>объектом, который реализует, в данном случае объект RDTExplorer.

8. Обновление метода утилизации RDTExplorerWindow()

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> удаляет соединение между `RDTExplorer` и уведомление мгновений события RDT.

9. Добавьте следующую строку <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> к телу `return` обработчика, непосредственно перед заявлением.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Добавьте аналогичную строку <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> к телу обработчика и к другим событиям, которые вы хотите увидеть в поле списка.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр Visual Studio.

12. Откройте **RDTExplorerWindow** **(Просмотр / Другие Окна / RDTExplorerWindow**).

     Окно **RDTExplorerWindow** открывается пустым списком событий.

13. Откройте или создайте решение.

     По `OnBeforeLastDocument` `OnAfterFirstDocument` мере того, как и события увольняются, в списке событий отображается уведомление о каждом событии.
