---
title: Доступ к объекту DTE из расширения редактора
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697664"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Прохождение: Доступ к объекту DTE из расширения редактора

В VSPackages можно получить объект DTE, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> позвонив по методу с типом объекта DTE. В расширениях Управляемой расширительности (MEF) <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> можно импортировать, а затем вызывать <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метод с типом <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="get-the-dte-object"></a>Получает объект DTE.

1. Создайте проект VSIX и назовите его **DTETest**. Добавьте шаблон элемента **классификатора редактора** и назовите его **DTETest**.

   Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Добавьте следующие ссылки на сборку проекта:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. В *DTETestProvider.cs* файле добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` классе импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` методе добавьте следующий `return` код перед заявлением:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Добавьте следующие ссылки на сборку проекта:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. В *DTETestProvider.cs* файле добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. В `DTETestProvider` классе импортируйте <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. В `GetClassifier()` методе добавьте следующий `return` код перед заявлением:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>См. также

- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Запуск Visual Studio с помощью DTE](launch-visual-studio-dte.md)
