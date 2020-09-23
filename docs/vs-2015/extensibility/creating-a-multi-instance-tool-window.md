---
title: Создание окна инструментов с несколькими экземплярами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dcdfe3f6e488514bb2ee1ca950e952b16039b42
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "91102528"
---
# <a name="creating-a-multi-instance-tool-window"></a>Создание многоэкземплярного окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно программировать окно инструментов, чтобы можно было одновременно открыть несколько экземпляров. По умолчанию окна инструментов могут открывать только один экземпляр.  
  
 При использовании многоэкземплярного окна инструментов можно одновременно отобразить несколько связанных источников информации. Например, можно разместить многострочный <xref:System.Windows.Forms.TextBox> элемент управления в многоэкземплярном окне инструментов, чтобы несколько фрагментов кода одновременно были доступны во время сеанса программирования. Кроме того, например, можно поместить <xref:System.Windows.Forms.DataGrid> элемент управления и раскрывающийся список в многоэкземплярном окне инструментов, чтобы несколько источников данных в реальном времени можно было одновременно контролировать.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Создание простого окна инструментов (с одним экземпляром)  
  
1. Создайте проект с именем **мултиинстанцетулвиндов** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструментов с именем **митулвиндов**.  
  
    > [!NOTE]
    > Дополнительные сведения о создании расширения с помощью окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Создание нескольких экземпляров окна инструментов  
  
1. Откройте файл **MIToolWindowPackage.CS** и найдите `ProvideToolWindow` атрибут. и `MultiInstances=true` параметр, как показано в следующем примере.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2. В файле MIToolWindowCommand.cs найдите метод Шовтулвиндос (). В этом методе вызовите <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и установите его `create` флаг `false` таким образом, чтобы он просматривает существующие экземпляры окна инструментов до тех пор, пока `id` не будет найдена доступная.  
  
3. Чтобы создать экземпляр окна инструментов, вызовите <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и присвойте ему `id` доступное значение и `create` флаг `true` .  
  
     По умолчанию значением `id` параметра <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метода является `0` . Это делает окно инструментов с одним экземпляром. Для размещения более чем одного экземпляра необходимо, чтобы каждый экземпляр был уникальным `id` .  
  
4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта, возвращаемого <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> свойством экземпляра окна инструментов.  
  
5. По умолчанию `ShowToolWindow` метод, созданный с помощью шаблона элемента окна инструментов, создает окно инструмента с одним экземпляром. В следующем примере показано, как изменить `ShowToolWindow` метод для создания нескольких экземпляров.  
  
    ```csharp  
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
