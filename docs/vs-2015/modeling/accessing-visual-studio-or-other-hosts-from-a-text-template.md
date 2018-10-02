---
title: Доступ к Visual Studio или другим ведущим приложениям из текстового шаблона | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5bcd1811db000b39f7c9897f1329434af9fe5258
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562956"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Обращение к Visual Studio или другим ведущим приложениям из текстового шаблона
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [доступ к Visual Studio или другие узлы из текстового шаблона](https://docs.microsoft.com/visualstudio/modeling/accessing-visual-studio-or-other-hosts-from-a-text-template).  
  
В текстовом шаблоне, можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон, такой как [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Это относится к шаблонам обычный текст, не предварительно обработанных текстовых шаблонах.  
  
## <a name="obtaining-access-to-the-host"></a>Получение доступа к узлу  
 Задайте `hostspecific="true"` в `template` директива. Это позволяет использовать `this.Host`, который имеет тип <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Этот тип содержит члены, которые можно использовать, например, для разрешения имен файлов и для ведения журнала ошибок.  
  
### <a name="resolving-file-names"></a>Разрешение имен файлов  
 Чтобы найти полный путь к файлу относительно текстового шаблона, используйте это. Host.ResolvePath().  
  
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
  
### <a name="displaying-error-messages"></a>Отображение сообщения об ошибках  
 Этот пример записывает сообщения, при преобразовании шаблона. Если узел работает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], они добавляются в окне ошибок.  
  
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
  
## <a name="using-the-visual-studio-api"></a>С помощью API Visual Studio  
 При выполнении текстового шаблона в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно использовать `this.Host` для доступа к службам, предоставляемые [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и пакеты или расширения, которые загружаются.  
  
 Значение hostspecific = «true» и приведите `this.Host` для <xref:System.IServiceProvider>.  
  
 В этом примере извлекаются [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, как служба:  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>С помощью hostSpecific с наследованием шаблона  
 Укажите `hostspecific="trueFromBase"` при использовании `inherits` атрибут, и при наследовании из шаблона, который указывает `hostspecific="true"`. Это позволяет избежать предупреждения компилятора с эффектом, свойство `Host` объявляется дважды.



