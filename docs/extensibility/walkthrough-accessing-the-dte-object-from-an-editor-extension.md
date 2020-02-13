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
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269091"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Пошаговое руководство. доступ к объекту DTE из расширения редактора

В VSPackage можно получить объект DTE, вызвав метод <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> с типом объекта DTE. В расширениях Managed Extensibility Framework (MEF) можно импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>, а затем вызвать метод <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> с типом <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prerequisites

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Получает объект DTE.

1. Создайте проект C# VSIX и назовите его **дтетест**. Добавьте шаблон элемента **классификатора редактора** и назовите его **дтетест**.

   Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Добавьте в проект следующие ссылки на сборки:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. неизменяемый. 10.0

3. В файл *DTETestProvider.CS* добавьте следующие директивы `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В классе `DTETestProvider` импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В методе `GetClassifier()` добавьте следующий код перед инструкцией `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Добавьте в проект следующие ссылки на сборки:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. В файл *DTETestProvider.CS* добавьте следующие директивы `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В классе `DTETestProvider` импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В методе `GetClassifier()` добавьте следующий код перед инструкцией `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>См. также:

- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Запуск Visual Studio с помощью DTE](launch-visual-studio-dte.md)
