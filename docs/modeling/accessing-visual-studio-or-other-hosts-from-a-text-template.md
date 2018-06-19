---
title: Обращение к Visual Studio или другим ведущим приложениям из текстового шаблона
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 657abba976e0f0d167651943289296d340981e62
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946521"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Доступ к Visual Studio или другим основным приложениям из текстового шаблона

В текстовом шаблоне можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон. Visual Studio является примером узла.

> [!NOTE]
> Можно использовать узел методов и свойств в шаблонах обычный текст, но не в *предварительно* текстовых шаблонов.

## <a name="obtain-access-to-the-host"></a>Получить доступ к узлу

Для доступа к узлу, задайте `hostspecific="true"` в `template` директивы. Теперь вы можете использовать `this.Host`, имеющий тип <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Тип содержит члены, которые можно использовать, например, для разрешения имен файлов и журнал ошибок.

### <a name="resolve-file-names"></a>Разрешения имен файлов

Чтобы найти полный путь к файлу относительно текстового шаблона, используйте `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Отображать сообщения об ошибках

В этом примере сообщения записываются при преобразовании шаблона. Если узел находится в Visual Studio, ошибки будут добавлены **список ошибок**.

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

## <a name="use-the-visual-studio-api"></a>С помощью Visual Studio API

Если текстовый шаблон выполняется в Visual Studio, можно использовать `this.Host` для доступа к службам, предоставляемые Visual Studio и любых пакетов или загружаемые расширения.

Значение hostspecific = «true» и приведите `this.Host` для <xref:System.IServiceProvider>.

В этом примере извлекаются Visual Studio API <xref:EnvDTE.DTE>, как служба:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Используйте hostSpecific с наследованием шаблона

Укажите `hostspecific="trueFromBase"` при использовании `inherits` атрибут, и при наследовании от шаблона, указывающего `hostspecific="true"`. Если этого не сделать, может появиться предупреждение, компилятора, свойство `Host` объявляется дважды.