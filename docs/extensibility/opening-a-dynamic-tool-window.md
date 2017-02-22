---
title: "Открытие окна динамическое средство | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "динамические окна инструментов"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Открытие окна динамическое средство
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Средство windows обычно открываются из команды в меню или эквивалентные сочетания клавиш. В некоторых случаях Однако, может потребоваться окна инструментов, которое открывает всякий раз, когда применяется определенного контекста пользовательского интерфейса и закрывается при больше не применяется контекст пользовательского интерфейса. Окна инструментов, как они называются *динамическое* или *автоматически отображается*.  
  
> [!NOTE]
>  Список предварительно определенных контекстах пользовательского интерфейса см. в разделе <xref:Microsoft.VisualStudio.VSConstants.UIContext>. Для  
  
 Если вы хотите открыть окно динамическое средство во время запуска, а также возможен сбой при создании, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> интерфейса и проверки условий сбоя в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> метод. Чтобы знать, что имеется динамическое средство окна, должен быть открыт при запуске оболочки, необходимо добавить `SupportsDynamicToolOwner` значение \(1\) в регистрации пакета. Это значение не является частью стандарта <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, поэтому необходимо создать настраиваемый атрибут, чтобы добавить его. Дополнительные сведения о настраиваемых атрибутах см. в разделе [Использование пользовательского атрибута регистрации для регистрации расширения](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension).  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для открытия окна средства. Окно инструментов создается при необходимости.  
  
> [!NOTE]
>  Динамическое средство окно может быть закрыто пользователем. Если вы хотите создать команду меню, поэтому пользователь может повторно открыть окно инструментов, в том же контексте пользовательского интерфейса, откроется окно инструментов и отключена в противном случае следует использовать команды меню.  
  
### Чтобы открыть окно динамическое средство  
  
1.  Создайте проект VSIX с именем **DynamicToolWindow** и добавление шаблона элемента окна средства с именем **DynamicWindowPane.cs**. Для получения дополнительной информации см. [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  В файле DynamicWindowPanePackage.cs найдите объявление DynamicWindowPanePackage. Добавление <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute атрибуты для регистрации окно инструментов.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     При этом регистрируется окно инструментов с именем DynamicWindowPane как временные окна, не сохраняются при закрытии и повторном открытии Visual Studio. Открыть DynamicWindowPane всякий раз, когда <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> применяется и закрыт, в противном случае.  
  
3.  Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен отображаться. Вы не увидите окно инструментов.  
  
4.  Откройте проект в экспериментальном экземпляре. Должно появиться окно инструментов.