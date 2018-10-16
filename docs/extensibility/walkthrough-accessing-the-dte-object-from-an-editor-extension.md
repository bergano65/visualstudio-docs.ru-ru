---
title: 'Пошаговое руководство: Доступ к объекту DTE из расширения редактора | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ed4343139b3e59dfba7adc71b1c91cdf01c13db
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586252"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Пошаговое руководство: Доступ к объекту DTE из расширения редактора
В пакеты VSPackage, можно получить объект DTE вызвав <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод с типом объекта DTE. В расширениях Managed Extensibility Framework (MEF), вы можете импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , а затем вызвать <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод с типом <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Получение объекта DTE  
  
### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Чтобы получить объект DTE из ServiceProvider  
  
1.  Создайте проект VSIX C# с именем `DTETest`. Добавьте шаблон элемента классификатора редактора и назовите его `DTETest`. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Добавьте следующие ссылки на сборки в проект:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Перейдите к *DTETest.cs* файла и добавьте следующие `using` директивы:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  В `GetDTEProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Добавьте в метод `GetClassifier()` следующий код:  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Если необходимо использовать <xref:EnvDTE80.DTE2> интерфейс, можно привести объект DTE к нему.  
  
## <a name="see-also"></a>См. также  
 [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)