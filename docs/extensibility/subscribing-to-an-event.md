---
title: Подписка на событие | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41ed19cb31924e90ef9326aad5c8cad117996793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141907"
---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом руководстве описывается создание окна инструментов, которое реагирует на события в запущенной таблице документов (RDT). Окно инструментов размещается пользовательский элемент управления, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Метод подключает интерфейс к событиям.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Подписка на события RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Для создания расширения с окном инструментов  
  
1.  Создайте проект с именем **RDTExplorer** с помощью шаблона VSIX и добавить шаблон элемента окна пользовательского инструмента с именем **RDTExplorerWindow**.  
  
     Дополнительные сведения о создании модуля с окном инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Чтобы подписаться на события RDT  
  
1.  Откройте файл RDTExplorerWindowControl.xaml и удалите кнопки с именем `button1`. Добавить <xref:System.Windows.Forms.ListBox> управления и примите имя по умолчанию. Элемент Grid должна выглядеть следующим образом:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Откройте файл RDTExplorerWindow.cs в представлении кода. Добавьте следующие инструкции using в начале файла.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Изменить `RDTExplorerWindow` класса, что не только производным от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класса, он реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> интерфейса.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Реализуйте интерфейс. Поместите курсор на имя IVsRunningDocTableEvents. Вы увидите лампочки в левом поле. Нажмите стрелку вниз справа от лампочку и выберите **реализовать интерфейс**.  
  
5.  В каждый метод в интерфейсе, замените строку `throw new NotImplementedException();` с этим:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Добавьте в класс RDTExplorerWindow поля файла cookie.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Содержит файл cookie, который возвращается методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> метод.  
  
7.  Переопределите метод Initialize() RDTExplorerWindow для регистрации событий RDT. Всегда следует получать службы в метод Initialize() ToolWindowPane, а не в конструкторе.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Служба вызывается для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Метод подключается RDT событий для объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, в этом случае объект RDTExplorer.  
  
8.  Метод Dispose() RDTExplorerWindow обновления.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Метод удаляет соединение между `RDTExplorer` и RDT уведомления о событиях.  
  
9. Добавьте следующую строку в текст <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> обработчик, непосредственно перед `return` инструкции.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Добавьте в тело похожая строка <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> обработчика и другие события, которые можно увидеть в списке.  
  
    ```csharp  
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
  
     Как `OnBeforeLastDocument` и `OnAfterFirstDocument` происходят события, уведомления о каждом событии в окне событий появляется список.