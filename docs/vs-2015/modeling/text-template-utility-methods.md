---
title: Служебные методы для текстовых шаблонов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0da69de4a91ebabce4af99e26195b349ef5daa60
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411414"
---
# <a name="text-template-utility-methods"></a>Служебные методы для текстовых шаблонов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует несколько методов, которые всегда доступны для вас при написании кода [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] текстового шаблона. Эти методы определяются в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
> Можно также использовать другие методы и служб, предоставляемых средой узла в шаблоне регулярных (без предварительной обработки) текста. Например, можно разрешить пути к файлам, ведения журнала ошибок и получить службы, предоставляемые [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и любой загруженных пакетов.  Дополнительные сведения см. в разделе [доступ к Visual Studio из текстового шаблона](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Написание методов  
 Можно использовать `Write()` и `WriteLine()` методы можно добавлять текст в стандартный блок кода, вместо использования блока кода выражения. В следующих блоках кода функционально эквивалентны.  
  
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
  
 Может оказаться полезным использовать один из этих служебных методов вместо блока выражения в длинном блоке кода с вложенные структуры управления.  
  
 `Write()` И `WriteLine()` методы имеют две перегруженные версии, одна из которых принимает один строковый параметр и один принимает строку составного формата, а также массив объектов для включения в строку (например `Console.WriteLine()` метод). Следующие два применения `WriteLine()` функционально эквивалентны:  
  
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
 Можно использовать методы отступа для форматирования вывода текстового шаблона. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Класс имеет `CurrentIndent` строковое свойство, которое отображает текущий отступ в текстовом шаблоне и `indentLengths` поле, то есть список отступы, которые были добавлены. Вы можете добавить отступ с `PushIndent()` метод и удалить отступ с `PopIndent()` метод. Если вы хотите удалить все отступы, используйте `ClearIndent()` метод. Следующий блок кода показано использование этих методов:  
  
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
  
 Этот блок кода выводит следующие результаты:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Методы ошибок и предупреждений  
 Ошибка "и" warning "Служебные методы можно использовать для добавления сообщений в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] список ошибок. Например следующий код будет добавить сообщение об ошибке в списке ошибок.  
  
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
  
## <a name="access-to-host-and-service-provider"></a>Доступ к узлу и поставщика услуг  
 Свойство `this.Host` можно предоставить доступ к свойствам, предоставляемым основным приложением, выполняющего шаблона. Чтобы использовать `this.Host`, необходимо задать `hostspecific` атрибут в `<@template#>` директивы:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Тип `this.Host` зависит от типа узла, в котором выполняется шаблон. В шаблоне, который выполняется в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно привести `this.Host` для `IServiceProvider` для получения доступа к службам, например интегрированной среды разработки. Пример:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>С помощью другой набор служебных методов  
 Как часть в процессе создания текста, файл шаблона преобразуется в класс, который всегда имеет имя `GeneratedTextTransformation`и наследует от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Если вы хотите использовать другой набор методов, можно написать собственный класс и укажите его в директиве template. Этот класс должен наследовать из <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Используйте `assembly` директива для ссылки на сборку, где находится скомпилированный класс.
