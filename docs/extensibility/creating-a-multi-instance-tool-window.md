---
title: "Создание многоэкземплярного окна средства | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Multi"
  - "окна инструментов"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Создание многоэкземплярного окна средства
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Окно инструментов можно запрограммировать так, что несколько экземпляров могут быть открыты одновременно. По умолчанию средство windows может иметь только один экземпляр открыть.  
  
 При использовании многоэкземплярного окна средства можно отобразить несколько связанных источников информации, в то же время. Например, можно поместить несколько строк <xref:System.Windows.Forms.TextBox> многоэкземплярного окна средства управления, чтобы несколько доступных фрагментов одновременно во время программирования сеанса. Кроме того, например, можно поместить <xref:System.Windows.Forms.DataGrid> управления и раскрывающегося списка поле в окне инструментов несколькими экземплярами, чтобы одновременно может отслеживаться несколько источников данных в режиме реального времени.  
  
## Создание окна средства Basic \(экземпляра\)  
  
1.  Создайте проект с именем **MultiInstanceToolWindow** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **MIToolWindow**.  
  
    > [!NOTE]
    >  Дополнительные сведения о создании модуля с окном инструмента см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Создание нескольких экземпляров окна инструментов  
  
1.  Откройте **MIToolWindowPackage.cs** файл и найдите `ProvideToolWindow` атрибута. и `MultiInstances=true` параметра, как показано в следующем примере.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  В файле MIToolWindowCommand.cs найдите метод ShowToolWindos\(\). В этом методе можно вызывать <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и набор его `create` флаг `false` таким образом, он будет выполнять итерацию существующих экземпляров окна средства до доступного `id` найден.  
  
3.  Чтобы создать экземпляр окна, вызовите <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и задайте его `id` для доступных значений и его `create` флаг `true`.  
  
     По умолчанию значение `id` параметр <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод `0`. Это делает окно инструментов с одним экземпляром. Для более чем одного экземпляра размещать каждый экземпляр должен иметь свой собственный уникальный `id`.  
  
4.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта, возвращенного <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Свойства экземпляра окна средства.  
  
5.  По умолчанию `ShowToolWindow` метод, созданный с помощью шаблона элемента окна средство создает окно инструментов с одним экземпляром. Следующий пример демонстрирует изменение `ShowToolWindow` метод для создания нескольких экземпляров.  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```