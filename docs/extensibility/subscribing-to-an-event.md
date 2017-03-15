---
title: "Подписка на событие | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
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
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом руководстве описывается создание окна средства, реагирующего на события в выполняемой таблице документа (RDT). Окно инструментов содержит пользовательский элемент управления, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Подключается интерфейс событий.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Подписка на события RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Для создания расширения с окном инструментов  
  
1.  Создайте проект с именем **RDTExplorer** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **RDTExplorerWindow**.  
  
     Дополнительные сведения о создании модуля с окном инструмента см. в разделе [создания расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Подписка на события RDT  
  
1.  Откройте файл RDTExplorerWindowControl.xaml и удалить кнопку с именем `button1`. Добавление <xref:System.Windows.Forms.ListBox>управления и примите имя по умолчанию.</xref:System.Windows.Forms.ListBox> Элемент Grid должен выглядеть следующим образом:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Откройте файл RDTExplorerWindow.cs в представлении кода. Добавьте следующие операторы using в начало файла.  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Изменить `RDTExplorerWindow` класса, что помимо наследование от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>реализует класс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>интерфейс.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   Реализуйте интерфейс. Поместите курсор на имя IVsRunningDocTableEvents. Вы должны увидеть лампочка в левом поле. Щелкните стрелку вниз справа от лампочки и выберите **реализовать интерфейс**.  
  
5.  Замените строку в каждый метод в интерфейсе `throw new NotImplementedException();` с этим:  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Добавьте в класс RDTExplorerWindow поля файла cookie.  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     Содержит файл cookie, который возвращается <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
7.  Переопределите метод Initialize() RDTExplorerWindow для регистрации событий RDT. Всегда следует получать службы в метод Initialize() ToolWindowPane, а не в конструкторе.  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Службы вызывается, чтобы получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Подключается RDT события объект, реализующий интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, в этом случае объект RDTExplorer.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
8.  Обновите метод Dispose() RDTExplorerWindow.  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>Метод удаляет соединение между `RDTExplorer` и уведомления о событиях RDT.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>  
  
9. Добавьте следующую строку в тексте <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>обработчика, непосредственно перед `return` инструкции.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Добавьте в текст похожая строка <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>обработчик и для других событий, которые вы хотите увидеть в списке.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
12. Откройте **RDTExplorerWindow** (**представления и других окон или RDTExplorerWindow**).  
  
     **RDTExplorerWindow** откроется окно со списком пустое событие.  
  
13. Откройте или создайте решение.  
  
     Как `OnBeforeLastDocument` и `OnAfterFirstDocument` события запускаются, уведомление о каждом событии в событии появляется список.
