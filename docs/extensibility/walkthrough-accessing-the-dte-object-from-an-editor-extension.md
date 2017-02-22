---
title: "Пошаговое руководство: Доступ к объекту DTE из расширение редактора | Microsoft Docs"
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
  - "редакторы [Visual Studio SDK] новый - получение объекта DTE"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Доступ к объекту DTE из расширение редактора
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В пакеты VSPackage, можно получить объект DTE, вызвав <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод с типом объекта DTE. В расширениях Managed Extensibility Framework \(MEF\), можно импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> а затем вызвать <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод с типом <xref:EnvDTE.DTE>.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Получение объекта DTE  
  
#### Чтобы получить объект DTE из поставщик службы  
  
1.  Создайте проект VSIX C\# с именем `DTETest`. Добавьте шаблон элемента редактор классификатора и назовите его `DTETest`. Для получения дополнительной информации см. [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Добавьте ссылки на следующие сборки в проект:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Перейдите к файлу DTETest.cs и добавьте следующие `using` директивы:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  В `GetDTEProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Добавьте в метод `GetClassifier()` следующий код:  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Если необходимо использовать <xref:EnvDTE80.DTE2> интерфейс, можно привести к нему объект DTE.  
  
## См. также  
 [Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)