---
title: Создание и управление ими модальные диалоговые окна | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfd0fb71aaca9cb3de2d7cc6d3b6229042a4e7fa
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318411"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Создание и управление ими модальные диалоговые окна
При создании модального диалогового окна в Visual Studio, необходимо убедитесь в том, что родительское окно окна отключен во время отображения диалогового, а затем повторно включить родительского окна, после закрытия окно. Если этого не сделать, появляется сообщение об ошибке: *Microsoft Visual Studio не удается завершить работу, так как модальное диалоговое окно является активным. Закройте это окно и повторите попытку.*

Это можно сделать двумя способами. Если диалоговое окно WPF, рекомендуется наследование из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем вызвать <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> отображать диалоговое окно. После этого вы не обязательно должны управлять модальное состояние родительского окна.

Если диалоговое окно не является WPF, или для другой причине, не может быть производным диалогового окна класса из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем родительского диалогового окна необходимо получить, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> и управлять модального состояния самостоятельно, путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> метод с параметр 0 (false), перед открытием окна и вызов метода снова с параметром 1 (true) после закрытия диалогового окна.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Создание диалогового окна, производного от DialogWindow

1. Создайте проект VSIX с именем **OpenDialogTest** и добавьте команду меню с именем **OpenDialog**. Дополнительные сведения о том, как это сделать, см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Чтобы использовать <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> класса, необходимо добавить ссылки на следующие сборки (на вкладке «платформы» **добавить ссылку** диалоговое окно):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. В *OpenDialog.cs*, добавьте следующий `using` инструкции:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Объявите класс с именем `TestDialogWindow` , наследуемый от класса <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Чтобы обеспечить свернуть или развернуть окно, задайте <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> и <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> значение true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. В `OpenDialog.ShowMessageBox` метод, замените существующий код следующим:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Выполните сборку и запуск приложения. Откроется экспериментальный экземпляр Visual Studio. На **средства** меню экспериментального экземпляра вы увидите команду с именем **вызвать OpenDialog**. При выполнении этой команды вы увидите диалоговое окно. Можно свести к минимуму и полностью развернуть окно.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Создание и управление ими диалоговое окно, не являющиеся производными DialogWindow

1. Для выполнения этой процедуры можно использовать **OpenDialogTest** решение, созданное в предыдущей процедуре, с тем же ссылки на сборки.

2. Добавьте следующий `using` объявления:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Создайте класс с именем `TestDialogWindow2` , наследуемый от класса <xref:System.Windows.Window>:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Добавьте ссылку на закрытый <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```
    private IVsUIShell shell;
    ```

5. Добавьте конструктор, который задает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. В `OpenDialog.ShowMessageBox` метод, замените существующий код следующим:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Выполните сборку и запуск приложения. На **средства** меню вы увидите команду с именем **вызвать OpenDialog**. При выполнении этой команды вы увидите диалоговое окно.
