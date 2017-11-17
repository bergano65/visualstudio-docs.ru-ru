---
title: "Служебные методы для текстовых шаблонов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 534a7317b4bca2abe559c028d025a52997a9f508
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="text-template-utility-methods"></a>Служебные методы для текстовых шаблонов
Существует несколько методов, всегда будут доступны пользователю при написании кода [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] текстового шаблона. Эти методы определяются в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Можно также использовать другие методы и службы, предоставляемые средой размещения в шаблоне обычный текст (без предварительной обработки). Например, разрешения путей к файлам, журнал ошибок и получения служб, предоставляемых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и любыми загруженными пакетами.  Дополнительные сведения см. в разделе [доступ к Visual Studio из текстового шаблона](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Написать методы  
 Можно использовать `Write()` и `WriteLine()` методы можно добавлять текст в стандартный блок кода, вместо использования блока кода выражения. Следующие два блока кода функционально эквивалентны.  
  
##### <a name="code-block-with-an-expression-block"></a>Блок кода с блоком выражения  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Блок кода, с помощью WriteLine()  
  
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
  
 `Write()` И `WriteLine()` методы имеют две перегруженные версии, одна из которых принимает один строковый параметр и одно принимает строки составного формата, а также массив объектов для включения в строку (например `Console.WriteLine()` метода). Следующие два применения `WriteLine()` функционально эквивалентны:  
  
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
  
## <a name="indentation-methods"></a>Методы для отступов  
 Отступ методы можно использовать для форматирования выходных данных текстовый шаблон. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Класс имеет `CurrentIndent` строковое свойство, которое отображает текущий отступ в текстовом шаблоне и `indentLengths` поле, список отступы, которые были добавлены. Можно добавить отступ с `PushIndent()` метод и удалить отступ с `PopIndent()` метод. Для удаления всех отступов, используйте `ClearIndent()` метод. Следующий блок кода показано использование этих методов.  
  
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
  
 Этот блок кода выводятся следующие данные:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Методы ошибок и предупреждений  
 Ошибки и предупреждения служебные методы можно использовать для добавления сообщений в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] список ошибок. Например следующий код будет добавлен сообщение об ошибке в списке ошибок.  
  
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
  
## <a name="access-to-host-and-service-provider"></a>Доступ к узла и поставщик услуг  
 Свойство `this.Host` позволяют осуществлять доступ к свойствам узла, выполняющего шаблона. Для использования `this.Host`, необходимо задать `hostspecific` атрибута в `<@template#>` директиву:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Тип `this.Host` зависит от типа узла, в котором выполняется шаблон. В шаблоне, который выполняется в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно привести `this.Host` для `IServiceProvider` для получения доступа к службам, например интегрированной среды разработки. Например:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>С помощью другой набор служебных методов  
 В рамках процесса создания текстового файла шаблона преобразуется в класс, который всегда имеет имя `GeneratedTextTransformation`и наследует от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Если вы хотите использовать другой набор методов, можно написать собственный класс и укажите его в директиве template. Этот класс должен наследовать из <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Используйте `assembly` директивы для ссылки на сборку, где можно найти скомпилированного класса.