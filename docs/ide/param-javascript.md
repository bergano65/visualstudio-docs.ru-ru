---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML-тег JavaScript <param>"
  - "param - XML-тег JavaScript"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет сведения о документации для параметра в функции или метода.  
  
## Синтаксис  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### Параметры  
 `name`  
 Обязательный.  Имя параметра.  
  
 `type`  
 Необязательный.  Тип данных параметра.  Тип может быть одним из следующих:  
  
-   Тип языка ECMAScript в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
-   Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
-   Функция конструктора JavaScript.  
  
 `integer`  
 Необязательный.  Если свойство `type` имеет значение `Number`, указывает ли параметр целое число.  Установите значение `true`, чтобы указать, что параметр целое число; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `domElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `type` имеет приоритет над этим атрибутом.  Этот атрибут определяет, является ли параметр документированный элемента DOM.  Задайте значение `true` для указания того, что параметр элемента DOM; в противном случае укажите значение `false`.  Если атрибут `type` не задан, а параметр `domElement` имеет значение `true`, то IntelliSense обрабатывает документированный параметр как `HTMLElement` при выполнении завершение операторов.  
  
 `mayBeNull`  
 Необязательный.  Определяет, является ли документированный параметр может иметь значение NULL.  Установите значение `true`, чтобы указать, что параметр может иметь значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementType`  
 Необязательный.  Если `type` имеет значение `Array`, то этот атрибут определяет тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный.  Если `type``Array` и `elementType``Number`, то этот атрибут определяет, является ли элементы массива целые числа.  Установите значение `true`, чтобы указать, что элементы массива целые числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementDomElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `elementType` имеет приоритет над этим атрибутом.  Если `type` имеет значение `Array`, то этот атрибут определяет, является ли элементы массива элементов DOM.  Задайте значение `true` для указания того, что элементы элементов DOM; в противном случае укажите значение `false`.  Если атрибут `elementType` не задан, а параметр `elementDomElement` имеет значение `true`, то IntelliSense обрабатывает каждый элемент массива как `HTMLElement` при выполнении завершение операторов.  
  
 `elementMayBeNull`  
 Необязательный.  Если свойство `type` имеет значение `Array`, указывает ли элементы массива можно задать значение NULL.  Установите значение `true`, чтобы указать, что элементы массива можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `locid`  
 Необязательный.  Идентификатор для данных о параметре локализации.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в элементе [\<loc\>](../ide/loc-javascript.md).  
  
 `parameterArray`  
 Необязательный.  Определяет, является ли параметр документированный может быть повторено в вызове функции, аналогично итерации параметры, поддерживаемые в функции `String.format`.  Установите значение `true`, чтобы указать, что параметр может быть; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `optional`  
 Необязательный.  Определяет, является ли параметр является необязательным документированный в вызывающей функции.  Установите значение `true`, чтобы указать, что параметр является необязательным; в противном случае укажите значение `false`.  
  
 `value`  
 Необязательный.  Указывает код, который должен использоваться для оценки для использования самого IntelliSense вместо кода функции.  Этот атрибут можно использовать для предоставления сведений о типе, если тип параметра не указан.  Например, можно использовать тип параметра `value=’1’` выводится в виде числа.  
  
 `description`  
 Необязательный.  Описание параметра.  
  
## Заметки  
 Один обязательный атрибут `name`.  Все остальные атрибуты являются необязательными.  
  
 Элементы, используемые для создания заметок к функции, например [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) и [\<returns\>](../ide/returns-javascript.md), должен быть помещен в теле функции перед всеми выписками.  
  
 Если несколько элементов `<param>`, имеют одинаковые имена, один из элементов используется `<param>` и резервные элементы игнорируются.  Расширение функциональности, определяет, какой элемент используется не определено.  Если `name` ссылается на несуществующий параметр, элемент не учитывается.  
  
## Пример  
 В следующем примере кода показано, как использовать элемент `<param>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)