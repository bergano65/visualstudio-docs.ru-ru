---
title: "Открытие окна инструментов динамического | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 197bda3f825d0e709c1bc9ae08d8f0018b8b07c5
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2018
---
# <a name="opening-a-dynamic-tool-window"></a>Открытие окна инструментов динамического
Окна инструментов обычно открываются из команды меню или соответствующих сочетаний клавиш. В некоторых случаях Однако может потребоваться окна инструментов, которое открывается при каждом определенного контекста пользовательского интерфейса применяется и закрывается при контекст пользовательского интерфейса больше не применяется. Эти типы окон инструментов называются *динамическое* или *автоматическим отображением*.  
  
> [!NOTE]
>  Список предварительно определенных контекстах пользовательского интерфейса см. в разделе <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Для  
  
 Если вы хотите открыть окно инструментов динамического во время запуска и существует возможность создания сбой, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> интерфейса и проверки условий сбоя в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> метод. Оболочка при наличии окна динамического инструментов, которое должен быть открыт при запуске, вам необходимо добавить `SupportsDynamicToolOwner` значение (1) в пакет регистрации. Это значение не является частью стандарта <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, поэтому необходимо создать пользовательский атрибут, чтобы добавить его. Дополнительные сведения о настраиваемых атрибутах см. в разделе [с помощью пользовательского атрибута регистрации для регистрации расширения](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для открытия окна инструментов. При необходимости создания окна инструментов.  
  
> [!NOTE]
>  Можно закрыть окно инструментов динамического пользователем. Если вы хотите создать команду меню, поэтому пользователь может повторно открыть окно инструментов, в том же контексте пользовательского интерфейса, что окно инструментов, а в противном случае значение disabled должно быть включено команду меню.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Чтобы открыть окно инструментов динамического  
  
1.  Создайте проект VSIX с именем **DynamicToolWindow** и добавить шаблон элемента окно инструментов с именем **DynamicWindowPane.cs**. Дополнительные сведения см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Найдите в файле DynamicWindowPanePackage.cs DynamicWindowPanePackage объявления. Добавить <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> атрибутов, чтобы зарегистрировать окно инструментов.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Атрибуты выше зарегистрировать окно инструментов с именем DynamicWindowPane в качестве временного окна, размеры которого не сохраняется после повторного открытия Visual Studio. Открыть DynamicWindowPane всякий раз, когда <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> применяется и закрыт, в противном случае.  
  
3.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр. Вы не увидите окна инструментов.  
  
4.  В экспериментальном экземпляре откройте проект. Должно появиться окно инструментов.