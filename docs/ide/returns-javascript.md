---
title: "&lt;returns&gt; (JavaScript) | Microsoft Docs"
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
  - "returns - XML-тег JavaScript"
  - "XML-тег JavaScript <returns>"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет сведения о документации по результата функции или вызова метода.  
  
## Синтаксис  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### Параметры  
 `type`  
 Необязательный.  Тип данных возвращаемого значения.  Тип может быть одним из следующих:  
  
-   Тип языка ECMAScript в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
-   Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
-   Функция конструктора JavaScript.  
  
 `integer`  
 Необязательный.  Если свойство `type` имеет значение `Number`, указывает ли возвращаемое значение целого числа.  Задайте значение `true` для указания, что возвращаемое значение целого числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `domElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `type` имеет приоритет над этим атрибутом.  Этот атрибут задает ли документированное возвращаемое значение элемента DOM.  Задайте значение `true` для указания того, что возвращаемое значение элемента DOM; в противном случае укажите значение `false`.  Если атрибут `type` не задан, а параметр `domElement` имеет значение `true`, то IntelliSense обрабатывает документированное возвращаемое значение как `HTMLElement` при выполнении завершение операторов.  
  
 `mayBeNull`  
 Необязательный.  Определяет, является ли документированное возвращаемое значение может быть равно NULL.  Установите значение `true`, чтобы указать, что возвращаемое значение может быть равно NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementType`  
 Необязательный.  Если `type` имеет значение `Array`, то этот атрибут определяет тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный.  Если `type``Array` и `elementType``Number`, то этот атрибут определяет, является ли элементы массива целые числа.  Установите значение `true`, чтобы указать, что элементы массива целые числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementDomElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `elementType` имеет приоритет над этим атрибутом.  Если `type` имеет значение `Array`, то этот атрибут определяет, является ли элементы массива элементов DOM.  Задайте значение `true` для указания того, что элементы элементов DOM; в противном случае укажите значение `false`.  Если атрибут `elementType` не задан, а параметр `elementDomElement` имеет значение `true`, то IntelliSense обрабатывает каждый элемент массива как `HTMLElement` при выполнении завершение операторов.  
  
 `elementMayBeNull`  
 Необязательный.  Если свойство `type` имеет значение `Array`, указывает ли элементы массива можно задать значение NULL.  Установите значение `true`, чтобы указать, что элементы массива можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `locid`  
 Необязательный.  Идентификатор для данных локализации о возвращаемом значении.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в теге [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Необязательный.  Указывает код, который должен использоваться для оценки для использования самого IntelliSense вместо кода функции.  Например, этот атрибут можно использовать для предоставления IntelliSense для асинхронных обратных вызовов, например `Promise`.  Использование атрибута `value` с элементом `<returns>` может повысить производительность IntelliSense, вывод продолжительное выполнение кода.  
  
 `description`  
 Необязательный.  Описание возвращаемого значения.  
  
## Заметки  
 Элемент `<returns>` должен быть помещен в теле функции перед всеми выписками.  
  
## Пример  
 В следующем примере кода показано, как использовать элемент `<returns>`.  
  
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
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)