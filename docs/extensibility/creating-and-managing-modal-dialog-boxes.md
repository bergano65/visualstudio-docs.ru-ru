---
title: Создание и управление Модал Диалог Коробки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739491"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Создание и управление модальными диалоговые ящики
При создании модального диалогового окна внутри Visual Studio необходимо убедиться, что родительское окно диалогового окна отключено во время отображения диалогового окна, а затем повторно включить родительское окно после закрытия диалогового окна. Если вы этого не сделаете, вы можете получить ошибку: *Microsoft Visual Studio не может отключить, потому что модальный диалог активен. Закройте активный диалог и повторите попытку.*

Есть два способа сделать это. Рекомендуемый способ, если у вас есть wPF диалоговые окна, заключается в том, чтобы получить его из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем позвонить <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> для отображения диалогового окна. Если вы делаете это, вам не нужно управлять модальным состоянием родительского окна.

Если ваш диалоговый ящик не WPF, или по какой-либо <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>другой причине вы не можете получить ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> класс диалогового окна из, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> то вы должны получить родителей диалогового окна, позвонив и управлять модальным состоянием самостоятельно, позвонив метод с параметром 0 (ложный) перед отображением диалогового окна и вызывая метод снова с параметром 1 (правда) после закрытия диалогового окна.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Создание диалогового окна, полученного из DialogWindow

1. Создайте проект VSIX под названием **OpenDialogTest** и добавьте команду меню под названием **OpenDialog.** Для получения дополнительной информации о том, как это сделать, [см.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Чтобы использовать <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> класс, необходимо добавить ссылки на следующие сборки (в вкладке Framework в диалоговом окне **Добавления):**

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. В *OpenDialog.cs*добавьте `using` следующее заявление:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Объявить класс, названный, `TestDialogWindow` который происходит от: <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Чтобы иметь возможность свести к минимуму <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> и максимизировать диалоговую коробку, набор и правда:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. В `OpenDialog.ShowMessageBox` методе замените существующий код следующим:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Выполните сборку и запустите приложение. Экспериментальный экземпляр Visual Studio должен появиться. В меню **Инструментов** экспериментального экземпляра вы должны увидеть команду под названием **Invoke OpenDialog.** При нажатии на эту команду следует увидеть окно диалога. Вы должны быть в состоянии свести к минимуму и максимизировать окно.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Создание и управление диалоговое окно, не полученное из DialogWindow

1. Для этой процедуры можно использовать созданное в предыдущей процедуре решение **OpenDialogTest** с теми же ссылками на сборку.

2. Добавьте `using` следующие декларации:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Создайте класс, названный, `TestDialogWindow2` который происходит от: <xref:System.Windows.Window>

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Добавить частную <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ссылку на:

    ```
    private IVsUIShell shell;
    ```

5. Добавьте конструктор, который устанавливает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ссылку на:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. В `OpenDialog.ShowMessageBox` методе замените существующий код следующим:

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

7. Выполните сборку и запустите приложение. В меню **«Инструменты»** вы должны увидеть команду под названием **Invoke OpenDialog.** При нажатии на эту команду следует увидеть окно диалога.
