---
title: "Text Template Utility Methods | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, utility methods"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
caps.handback.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Text Template Utility Methods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Существует несколько методов, которые всегда доступны при написании кода в текстовом шаблоне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Эти методы определены в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Кроме того, в обычном \(без предварительной обработки\) текстовом шаблоне можно использовать и другие методы и службы, предоставляемые средой размещения.  Например, можно разрешать пути к файлам, заносить ошибки в журнал и использовать службы, предоставленные [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и любыми загруженными пакетами.  Дополнительные сведения см. в разделе [Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/ru-ru/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## Методы Write  
 С помощью методов `Write()` и `WriteLine()` можно добавлять текст в стандартный блок кода вместо использования блока кода выражения.  Приведенные далее два блока кода функционально эквивалентны.  
  
##### Блок кода с блоком выражения  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### Блок кода с использованием WriteLine\(\)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Может оказаться полезным использовать один из этих служебных методов вместо блока выражения в длинном блоке кода с вложенными управляющими структурами.  
  
 Методы `Write()` и `WriteLine()` имеют две перегруженные версии, одна из которых принимает один строковый параметр, а другая – строку сложного формата плюс массив объектов для включения в строку \(подобно методу `Console.WriteLine()`\).  Следующие два применения `WriteLine()` функционально эквивалентны:  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## Методы для отступов  
 С помощью методов, предназначенных для создания отступов, можно форматировать вывод текстового шаблона.  Класс <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> имеет строковое свойство `CurrentIndent`, которое отображает текущий отступ в текстовом шаблоне, и поле `indentLengths`, представляющее собой список добавленных отступов.  Можно добавить отступ с помощью метода `PushIndent()` и удалить отступ с помощью метода `PopIndent()`.  Для удаления всех отступов пользуйтесь методом `ClearIndent()`.  В следующем коде демонстрируется применение этих методов:  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 В результате выполнения данного блока кода получены следующие выходные данные.  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## Методы ошибок и предупреждений  
 Используя служебные методы ошибок и предупреждений, можно добавлять сообщения в список ошибок [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Например, следующий код добавляет в список ошибок сообщение об ошибке:  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## Доступ к основному приложений и поставщику услуг  
 Свойство `this.Host` может предоставлять доступ к свойствам. предоставляемым основным приложением, которое выполняет шаблон.  Для использования свойства `this.Host` необходимо установить атрибут `hostspecific` в директиве `<@template#>`:  
  
 `<#@template ...  hostspecific="true" #>`  
  
 Тип свойства `this.Host` зависит от типа основного приложения, в котором выполняется шаблон.  В шаблоне, который выполняется в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно привести `this.Host` к типу `IServiceProvider`, чтобы получить доступ к таким службам, как интерфейс IDE.  Примеры.  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## Использование другого набора служебных методов  
 В процессе генерирования текста файл шаблона преобразуется в класс, который всегда носит имя `GeneratedTextTransformation` и наследует <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  Если требуется использовать другой набор методов, можно написать собственный класс и задать его в директиве template.  Используемый класс должен наследовать <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Используйте директиву `assembly` для ссылки на сборку, в которой находится откомпилированный класс.