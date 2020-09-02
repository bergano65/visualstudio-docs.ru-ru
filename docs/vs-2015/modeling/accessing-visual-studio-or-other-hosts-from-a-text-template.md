---
title: Доступ к Visual Studio 2015 или другим узлам из текстового шаблона | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655326"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Обращение к Visual Studio или другим основным приложениям из текстового шаблона
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовом шаблоне можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон, например [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Это относится к обычным текстовым шаблонам, а не к предварительно обработанным текстовым шаблонам.

## <a name="obtaining-access-to-the-host"></a>Получение доступа к узлу

Задается `hostspecific="true"` в `template` директиве. Это позволяет использовать  `this.Host` , имеющий тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Этот тип содержит члены, которые можно использовать, например, для разрешения имен файлов и записи ошибок в журнал.

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
 В этом примере сообщения записываются при преобразовании шаблона. Если узел имеет значение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , они добавляются в окно ошибки.

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
 Если вы используете текстовый шаблон в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , можно использовать `this.Host` для доступа к службам, предоставляемым, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и любым загруженным пакетам или расширениям.

 Задайте hostspecific = "true" и приведите `this.Host` к типу <xref:System.IServiceProvider> .

 В этом примере в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] качестве службы получается API <xref:EnvDTE.DTE> :

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
 Укажите `hostspecific="trueFromBase"` , используется ли также `inherits` атрибут, и, если вы наследуете от шаблона, который указывает `hostspecific="true"` . Это позволяет избежать предупреждения о том, что свойство было `Host` объявлено дважды.
