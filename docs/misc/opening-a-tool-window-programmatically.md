---
title: "Открытие окна инструментов программным способом | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "окна инструментов, создание программным способом"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Открытие окна инструментов программным способом
Окна инструментов обычно открываются выбором команды в меню или нажатием соответствующих сочетаний клавиш. Тем не менее может потребоваться открыть окно инструментов программным путем, как это делает обработчик команд.  
  
 Чтобы открыть окно инструментов в управляемом пакете VSPackage, который его предоставляет, используйте метод <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>. Чтобы открыть окно инструментов в другом пакете VSPackage, используйте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>. В любом случае окно инструментов будет создано при необходимости.  
  
 Следующий код взят из примера Reference.ToolWindow на языке C\#.  
  
### Открытие окна инструментов программным способом  
  
1.  Создайте панель и фрейм окна инструментов и реализующий их пакет VSPackage. Для получения дополнительной информации см. [Добавление окна инструментов](../extensibility/adding-a-tool-window.md).  
  
2.  Добавьте атрибут <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> в пакет VSPackage, который его предоставляет.  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     Это действие регистрирует открытие окна инструментов PersistedWindowPane как закрепленного в **обозревателе решений**. Дополнительные сведения см. в разделе [Регистрация окна инструментов](../extensibility/registering-a-tool-window.md).  
  
3.  Используйте метод <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для поиска панели окна инструментов или ее создания, если она еще не существует.  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  Получите фрейм окна инструментов из панели окна инструментов.  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  Отобразите окно инструментов.  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```