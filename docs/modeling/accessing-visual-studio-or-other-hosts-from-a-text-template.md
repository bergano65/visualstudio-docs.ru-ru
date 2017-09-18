---
title: "Accessing Visual Studio or other Hosts from a Text Template | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 5
---
# Accessing Visual Studio or other Hosts from a Text Template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В текстовом шаблоне можно использовать методы и свойства, предоставленные узлом, на котором выполняется шаблон, например [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Это относится к обычным, а не предварительно обработанным текстовым шаблонам.  
  
## Получение адреса узла  
 Задайте значение `hostspecific="true"` в директиве `template`.  Это позволяет использовать `this.Host`, который имеет тип <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Члены этого типа можно использовать, например, для разрешения имен файлов и занесения ошибок в журнал.  
  
### Разрешение имен файлов  
 Чтобы найти полный путь к файлу относительно текстового шаблона, воспользуйтесь командой this.Host.ResolvePath\(\).  
  
```c#  
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
  
### Отображение сообщений об ошибках  
 В этом примере при преобразовании шаблона в журнал записываются сообщения.  Если узлом является [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], сообщения добавляются в окно ошибок.  
  
```c#  
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
  
## Использование API\-интерфейса Visual Studio  
 Если текстовый шаблон выполняется в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно воспользоваться `this.Host` для доступа к службам, предоставляемым [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], а также любым загруженным пакетам и расширениям.  
  
 Задайте значение hostspecific\="true" и выполните приведение `this.Host` к <xref:System.IServiceProvider>.  
  
 В этом примере API\-интерфейс [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:EnvDTE.DTE>, предоставляется как служба:  
  
```c#  
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
  
## С помощью hostSpecific с помощью шаблонов наследования  
 Укажите `hostspecific="trueFromBase"` при использовании также `inherits` атрибут, и при наследовании из шаблона, который определяет `hostspecific="true"`.  Это позволяет избежать предупреждения компилятора для эффекта, свойство `Host` был объявлен дважды.