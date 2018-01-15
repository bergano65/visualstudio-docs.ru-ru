---
title: "Доступ к Visual Studio или другим основным приложениям из текстового шаблона | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fa3f2c0a259afdb09f5565872c9c43c72f38e1c2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Обращение к Visual Studio или другим ведущим приложениям из текстового шаблона
В текстовом шаблоне можно использовать методы и свойства, предоставленные узлом, который выполняет шаблон, такие как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Это относится к шаблонам обычный текст, не обработанное текстовых шаблонов.  
  
## <a name="obtaining-access-to-the-host"></a>Получение доступа к узлу  
 Задать `hostspecific="true"` в `template` директивы. Это позволяет использовать `this.Host`, имеющий тип <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Этот тип содержит члены, которые можно использовать, например, для разрешения имен файлов и журнал ошибок.  
  
### <a name="resolving-file-names"></a>Разрешение имен файлов  
 Чтобы найти полный путь к файлу относительно текстового шаблона, можно используйте следующее. Host.ResolvePath().  
  
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
 В этом примере сообщения записываются при преобразовании шаблона. Если узел является [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], они добавляются в окно ошибок.  
  
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
  
## <a name="using-the-visual-studio-api"></a>С помощью Visual Studio API  
 При выполнении текстового шаблона в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно использовать `this.Host` для доступа к службам, предоставляемым [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и пакеты или загружаемые расширения.  
  
 Значение hostspecific = «true» и приведите `this.Host` для <xref:System.IServiceProvider>.  
  
 В этом примере извлекаются [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, как служба:  
  
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
 Укажите `hostspecific="trueFromBase"` при использовании `inherits` атрибут, и при наследовании от шаблона, указывающего `hostspecific="true"`. Это позволяет избежать Предупреждение компилятора эффекта, свойство `Host` объявляется дважды.