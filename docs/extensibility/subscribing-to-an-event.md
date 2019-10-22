---
title: Подписка на событие | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647920"
---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом руководстве объясняется, как создать окно инструментов, которое реагирует на события в выполняющейся таблице документов (РДТ). В окне инструментов размещается пользовательский элемент управления, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> подключает интерфейс к событиям.

## <a name="prerequisites"></a>Необходимые компоненты
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Подписка на события РДТ

#### <a name="to-create-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов

1. Создайте проект с именем **рдтексплорер** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструментов с именем **рдтексплорервиндов**.

     Дополнительные сведения о создании расширения с помощью окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Подписка на события РДТ

1. Откройте файл Рдтексплорервиндовконтрол. XAML и удалите кнопку с именем `button1`. Добавьте элемент управления <xref:System.Windows.Forms.ListBox> и примите имя по умолчанию. Элемент Grid должен выглядеть следующим образом:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Откройте файл RDTExplorerWindow.cs в представлении кода. Добавьте следующие директивы using в начало файла.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Измените класс `RDTExplorerWindow`, чтобы, помимо наследования от класса <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, он реализовал интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Реализуйте интерфейс. Поместите курсор на имя Ивсруннингдоктабливентс. В левом поле появится лампочка лампочки. Щелкните стрелку вниз справа от лампочки и выберите команду **реализовать интерфейс**.

5. В каждом методе в интерфейсе замените строку `throw new NotImplementedException();` следующим:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Добавьте поле cookie в класс Рдтексплорервиндов.

    ```csharp
    private uint rdtCookie;
    ```

     Он содержит файл cookie, возвращаемый методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Переопределите метод Initialize () Рдтексплорервиндов для регистрации событий РДТ. Всегда следует получать службы в методе Initialize () ToolWindowPane, а не в конструкторе.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Для получения интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> вызывается служба <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> соединяет события РДТ с объектом, реализующим <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> (в данном случае) объектом Рдтексплорер.

8. Обновите метод Dispose () Рдтексплорервиндов.

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

     Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> удаляет соединение между `RDTExplorer` и РДТ уведомления о событии.

9. Добавьте следующую строку в тело обработчика <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, непосредственно перед инструкцией `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Добавьте подобную строку в тело обработчика <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> и другие события, которые необходимо просмотреть в списке.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

12. Откройте **рдтексплорервиндов** (**представление/другие окна или рдтексплорервиндов**).

     Откроется окно **рдтексплорервиндов** с пустым списком событий.

13. Откройте или создайте решение.

     По мере срабатывания событий `OnBeforeLastDocument` и `OnAfterFirstDocument` в списке событий появляются уведомления о каждом событии.
