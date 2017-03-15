---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
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
  - "XML-тег JavaScript <var>"
  - "var - XML-тег JavaScript"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет сведения о документации для переменной.  
  
## Синтаксис  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### Параметры  
 `type`  
 Необязательный.  Тип данных переменной.  Тип может быть одним из следующих:  
  
-   Тип языка ECMAScript, в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
-   Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
-   Функция конструктора JavaScript.  
  
 `integer`  
 Необязательный.  Если свойство `type` имеет значение `Number`, указывает ли переменная целое число.  Установите значение `true`, чтобы указать, что переменная целое число; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `domElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `type` имеет приоритет над этим атрибутом.  Этот атрибут определяет, является ли документированная переменную элемента DOM.  Задайте значение `true` для указания того, что переменная элемента DOM; в противном случае укажите значение `false`.  Если атрибут `type` не задан, а параметр `domElement` имеет значение `true`, то IntelliSense обрабатывает документированную переменную как `HTMLElement` при выполнении завершение операторов.  
  
 `mayBeNull`  
 Необязательный.  Определяет, является ли документированную переменную можно задать значение NULL.  Задайте значение `true` для указания, что переменную можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementType`  
 Необязательный.  Если `type` имеет значение `Array`, то этот атрибут определяет тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный.  Если `type``Array` и `elementType``Number`, то этот атрибут определяет, является ли элементы массива целые числа.  Установите значение `true`, чтобы указать, что элементы массива целые числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementDomElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `elementType` имеет приоритет над этим атрибутом.  Если `type` имеет значение `Array`, то этот атрибут определяет, является ли элементы массива элементов DOM.  Задайте значение `true` для указания того, что элементы элементов DOM; в противном случае укажите значение `false`.  Если атрибут `elementType` не задан, а параметр `elementDomElement` имеет значение `true`, то IntelliSense обрабатывает каждый элемент массива как `HTMLElement` при выполнении завершение операторов.  
  
 `elementMayBeNull`  
 Необязательный.  Если свойство `type` имеет значение `Array`, указывает ли элементы массива можно задать значение NULL.  Установите значение `true`, чтобы указать, что элементы массива можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `helpKeyword`  
 Необязательный.  Ключевое слово для справки F1.  
  
 `locid`  
 Необязательный.  Идентификатор для данных о локализации переменной.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в теге [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Необязательный.  Описание переменной.  
  
## Пример  
 В следующем примере кода показано, как использовать элемент `<var>`.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)