---
title: Обращение к Visual Studio или другим основным приложениям из текстового шаблона
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd69ae5864df9cbddd204c45975736fc4aae49e5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597260"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Доступ к Visual Studio или другим узлам из текстового шаблона

В текстовом шаблоне можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон. Visual Studio приведен пример узла.

> [!NOTE]
> Можно использовать узел методы и свойства в шаблонах обычный текст, но не в *предварительно обработанные* текстовых шаблонов.

## <a name="obtain-access-to-the-host"></a>Получить доступ к узлу

Для доступа к узлу, задайте `hostspecific="true"` в `template` директива. Теперь можно использовать `this.Host`, имеющий тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) содержит члены, которые можно использовать для разрешения имен файлов и регистрации ошибок, например.

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

### <a name="display-error-messages"></a>Отображение сообщения об ошибках

Этот пример записывает сообщения, при преобразовании шаблона. Если узел находится Visual Studio, ошибки будут добавлены **список ошибок**.

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

## <a name="use-the-visual-studio-api"></a>Используйте API Visual Studio

Если текстовый шаблон выполняется в Visual Studio, можно использовать `this.Host` для доступа к службам, предоставляемые Visual Studio и пакеты или расширения, которые загружаются.

Значение hostspecific = «true» и приведите `this.Host` для <xref:System.IServiceProvider>.

В этом примере извлекаются Visual Studio API, <xref:EnvDTE.DTE>, как служба:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Использовать hostSpecific с наследованием шаблона

Укажите `hostspecific="trueFromBase"` при использовании `inherits` атрибут, и при наследовании из шаблона, который указывает `hostspecific="true"`. Если этого не сделать, может появиться предупреждение, свойство `Host` объявляется дважды.
