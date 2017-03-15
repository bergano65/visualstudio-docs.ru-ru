---
title: "Создание и управление модальные диалоговые окна | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1bb0372ab217847f91b1cdeeb8cf2915379e2f66
ms.lasthandoff: 02/22/2017

---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Создание и управление модальные диалоговые окна
При создании модального диалогового окна в Visual Studio, вы убедитесь в том, что родительского окна окно отключена, пока откроется диалоговое окно, затем повторно включить родительского окна после закрытия диалогового. Если этого не сделать, может появиться следующая ошибка: «Microsoft Visual Studio не удается завершить работу модальное диалоговое окно. Закройте это окно и повторите попытку.»  
  
 Это двумя способами. Если диалоговое окно WPF, рекомендуется наследование из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, а затем вызовите <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>для отображения диалогового окна.</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> После этого не требуется управлять модального состояния родительского окна.  
  
 Если диалоговое окно не является WPF или для любого другого класса причине нельзя наследовать диалогового окна <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, то родительского диалогового окна необходимо получить, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>и самостоятельно, управлять модальное состояние, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>метод с параметром 0 (false), прежде чем отображать диалоговое окно и вызов метода с параметром 1 (true) после закрытия диалогового окна.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Создание диалогового окна на основе DialogWindow  
  
1.  Создайте проект VSIX с именем **OpenDialogTest** и добавить команду меню с именем **OpenDialog**. Дополнительные сведения о том, как это сделать см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Для использования <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>класса, необходимо добавить ссылки на следующие сборки (на вкладке Framework **добавить ссылку** диалоговое окно):</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  Добавьте следующий код в OpenDialog.cs, `using` инструкции:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Объявите класс с именем **TestDialogWindow** , производный от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Чтобы иметь возможность свернуть или развернуть окно, задайте <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>и <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>значение true:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  В **OpenDialog.ShowMessageBox** метод, замените существующий код следующим:  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Выполните сборку и запуск приложения. Должна появиться экспериментальном экземпляре Visual Studio. На **средства** меню экспериментальный экземпляр вы должны увидеть команды с именем **OpenDialog вызова**. При выполнении этой команды вы увидите диалоговое окно. Можно свернуть и развернуть окно.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Создание и управление диалоговое окно не является производным от DialogWindow  
  
1.  Для выполнения этой процедуры можно использовать **OpenDialogTest** решение, созданное в предыдущей процедуре, с одной ссылки на сборки.  
  
2.  Добавьте следующие `using` объявления:  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Создайте класс с именем **TestDialogWindow2** , производный от <xref:System.Windows.Window>:</xref:System.Windows.Window>  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Добавьте закрытый ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Добавьте конструктор, который задает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  В **OpenDialog.ShowMessageBox** метод, замените существующий код следующим:  
  
    ```c#  
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
  
7.  Выполните сборку и запуск приложения. На **средства** меню вы должны увидеть команды с именем **OpenDialog вызова**. При выполнении этой команды вы увидите диалоговое окно.
