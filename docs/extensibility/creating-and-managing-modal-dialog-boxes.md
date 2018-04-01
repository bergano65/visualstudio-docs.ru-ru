---
title: Создание и управление ими модальные диалоговые окна | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc53145a52d6b902ef1b8d15195df37ee6de0d62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Создание и управление ими модальные диалоговые окна
При создании модального диалогового окна в Visual Studio, необходимо убедитесь в том, что родительское окно диалогового окна отключена, пока отображается диалоговое окно, а затем повторно включите родительского окна, после закрытия диалогового. Если это не так, может возникнуть ошибка: «Microsoft Visual Studio не может завершить работу активного модального диалогового окна. Закройте это окно и повторите попытку.»  
  
 Существует два способа это сделать. Если диалоговое окно WPF, рекомендуется наследование из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем вызвать метод <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> для отображения диалогового окна. После этого вы не обязательно должны управлять модальное состояние родительского окна.  
  
 Если диалоговое окно не является WPF или для любого другого класса причины, не может быть производным диалогового окна <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем родительского диалогового окна необходимо получить, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> и самостоятельно, управлять модальное состояние, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> метод с параметр 0 (false), прежде чем отображает диалоговое окно и вызов метода с параметром 1 (true) после закрытия диалогового окна.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Создание диалогового окна производными DialogWindow  
  
1.  Создайте проект VSIX с именем **OpenDialogTest** и добавьте команду меню с именем **OpenDialog**. Дополнительные сведения о том, как это сделать см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Для использования <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> класса, необходимо добавить ссылки на следующие сборки (на вкладке Framework **добавить ссылку** диалоговое окно «»):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  В OpenDialog.cs, добавьте следующий `using` инструкции:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Объявите класс с именем **TestDialogWindow** , производный от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Чтобы обеспечить свернуть или развернуть окно, задайте <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> и <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> значение true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  В **OpenDialog.ShowMessageBox** метод, замените существующий код следующим:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Выполните сборку и запуск приложения. Откроется экспериментальный экземпляр Visual Studio. На **средства** меню экспериментального экземпляра должна появиться команда **OpenDialog вызова**. При выполнении этой команды вы увидите диалоговое окно. Можно свернуть и развернуть окно.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Создание и управление ими диалоговое окно не является производным от DialogWindow  
  
1.  Для выполнения этой процедуры можно использовать **OpenDialogTest** решения, созданного в предыдущей процедуре, с одной ссылки на сборку.  
  
2.  Добавьте следующие `using` объявления:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Создайте класс с именем **TestDialogWindow2** , производный от <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Добавьте ссылку на закрытый <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Добавьте конструктор, который задает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  В **OpenDialog.ShowMessageBox** метод, замените существующий код следующим:  
  
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
  
7.  Выполните сборку и запуск приложения. На **средства** меню появится команда **OpenDialog вызова**. При выполнении этой команды вы увидите диалоговое окно.