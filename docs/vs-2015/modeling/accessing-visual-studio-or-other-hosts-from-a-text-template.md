---
title: Доступ к Visual Studio 2015 или другим узлам из текстового шаблона | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872009"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Обращение к Visual Studio или другим основным приложениям из текстового шаблона
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовом шаблоне можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон, например [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Это относится к обычным текстовым шаблонам, а не к предварительно обработанным текстовым шаблонам.

## <a name="obtaining-access-to-the-host"></a>Получение доступа к узлу

`hostspecific="true"` Задается `template` в директиве. Это позволяет использовать `this.Host`, имеющий тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Этот тип содержит члены, которые можно использовать, например, для разрешения имен файлов и записи ошибок в журнал.

### <a name="resolving-file-names"></a>Разрешение имен файлов
 Чтобы найти полный путь к файлу относительно текстового шаблона, используйте следующий текст. Host. Ресолвепас ().

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

### <a name="displaying-error-messages"></a>Отображение сообщений об ошибках
 Этот пример записывает сообщения, при преобразовании шаблона. Если узел имеет значение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], они добавляются в окно ошибки.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>

```

## <a name="using-the-visual-studio-api"></a>Использование API Visual Studio
 Если вы используете текстовый шаблон в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно использовать `this.Host` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для доступа к службам, предоставляемым, и любым загруженным пакетам или расширениям.

 Значение hostspecific = «true» и приведите `this.Host` для <xref:System.IServiceProvider>.

 В этом примере в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] качестве службы <xref:EnvDTE.DTE>получается API:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

```

## <a name="using-hostspecific-with-template-inheritance"></a>Использование hostSpecific с наследованием шаблонов
 Укажите `hostspecific="trueFromBase"` при использовании `inherits` атрибут, и при наследовании из шаблона, который указывает `hostspecific="true"`. Это позволяет избежать предупреждения о том, что свойство `Host` было объявлено дважды.
