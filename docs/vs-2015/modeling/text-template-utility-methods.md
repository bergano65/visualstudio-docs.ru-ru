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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658524"
---
# <a name="text-template-utility-methods"></a>Служебные методы для текстовых шаблонов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует несколько методов, которые всегда доступны при написании кода в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] текстовом шаблоне. Эти методы определяются в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Кроме того, можно использовать другие методы и службы, предоставляемые средой размещения, в обычном (не предварительно обработанном) текстовом шаблоне. Например, можно разрешить пути к файлам, вести журнал ошибок и получить службы, предоставляемые [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], и все загруженные пакеты.  Дополнительные сведения см. в разделе [доступ к Visual Studio из текстового шаблона](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Методы записи
 Можно использовать методы `Write()` и `WriteLine()` для добавления текста в стандартный блок кода вместо использования блока кода выражения. Следующие два блока кода функционально эквивалентны.

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

##### <a name="code-block-using-writeline"></a>Блок кода с помощью метода WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

 Может оказаться полезным использовать один из этих служебных методов вместо блока выражения внутри длинного блока кода с вложенными структурами элементов управления.

 Методы `Write()` и `WriteLine()` имеют две перегрузки, один из которых принимает один строковый параметр и один, принимающий строку составного формата плюс массив объектов для включения в строку (например, метод `Console.WriteLine()`). Следующие два применения `WriteLine()` функционально эквивалентны:

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

## <a name="indentation-methods"></a>Методы отступов
 Для форматирования выходных данных текстового шаблона можно использовать методы отступов. Класс <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> имеет `CurrentIndent` строкового свойства, показывающего текущий отступ в текстовом шаблоне, и поле `indentLengths`, которое представляет собой список добавленных отступов. Можно добавить отступ с помощью метода `PushIndent()` и вычесть отступ с помощью метода `PopIndent()`. Если необходимо удалить все отступы, используйте метод `ClearIndent()`. В следующем блоке кода показано использование следующих методов:

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

 Этот блок кода создает следующие выходные данные:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Методы error и Warning
 Для добавления сообщений в Список ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно использовать служебные методы ошибок и предупреждений. Например, следующий код добавит сообщение об ошибке в Список ошибок.

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

## <a name="access-to-host-and-service-provider"></a>Доступ к узлу и поставщику услуг
 Свойство `this.Host` может предоставлять доступ к свойствам, предоставляемым узлом, выполняющим шаблон. Чтобы использовать `this.Host`, необходимо задать атрибут `hostspecific` в директиве `<@template#>`:

 `<#@template ... hostspecific="true" #>`

 Тип `this.Host` зависит от типа узла, в котором выполняется шаблон. В шаблоне, который выполняется в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно привести `this.Host` к `IServiceProvider`, чтобы получить доступ к службам, таким как интегрированная среда разработки. Пример:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Использование другого набора служебных методов
 В рамках процесса формирования текста файл шаблона преобразуется в класс, который всегда называется `GeneratedTextTransformation`and наследуется от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Если вместо этого вы хотите использовать другой набор методов, можно написать собственный класс и указать его в директиве template. Класс должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

 Используйте директиву `assembly` для ссылки на сборку, в которой можно найти скомпилированный класс.
