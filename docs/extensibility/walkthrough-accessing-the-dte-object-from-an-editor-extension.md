---
title: Доступ к объекту DTE из расширения редактора
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fb22793c3bfa805fae11c8bbea7f07c06fd5a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322794"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Пошаговое руководство. Доступ к объекту DTE из расширения редактора

В пакеты VSPackage, можно получить объект DTE вызвав <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод с типом объекта DTE. В расширениях Managed Extensibility Framework (MEF), вы можете импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , а затем вызвать <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод с типом <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Получить объект DTE

1. Создание C# VSIX проект и назовите его **DTETest**. Добавить **классификатора редактора** шаблона элемента и назовите его **DTETest**.

   Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Добавьте следующую ссылку сборки в проект:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. В *DTETestProvider.cs* добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` метод, добавьте следующий код перед `return` инструкции:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Добавьте следующие ссылки на сборки в проект:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. В *DTETestProvider.cs* добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` метод, добавьте следующий код перед `return` инструкции:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>См. также

- [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)
- [Запустите Visual Studio, с помощью DTE](launch-visual-studio-dte.md)