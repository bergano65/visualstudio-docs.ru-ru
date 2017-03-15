---
title: "&lt;value&gt; (JavaScript) | Microsoft Docs"
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
  - "XML-тег JavaScript <value>"
  - "value - XML-тег JavaScript"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет сведения о документации для `get` и `set` для ECMAScript 3 свойства.  
  
## Синтаксис  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### Параметры  
 `type`  
 Необязательный.  Тип данных свойства.  Тип может быть одним из следующих:  
  
-   Тип языка ECMAScript, в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
-   Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
-   Функция конструктора JavaScript.  
  
 `integer`  
 Необязательный.  Если свойство `type` имеет значение `Number`, указывает, может ли свойство целое число.  Установите значение `true`, чтобы указать, что свойство целое число; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `domElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `type` имеет приоритет над этим атрибутом.  Этот атрибут задает ли документированное свойство элемента DOM.  Задайте значение `true` для указания того, что свойство элемента DOM; в противном случае укажите значение `false`.  Если атрибут `type` не задан, а параметр `domElement` имеет значение `true`, то IntelliSense обрабатывает документированное свойства как `HTMLElement` при выполнении завершение операторов.  
  
 `mayBeNull`  
 Необязательный.  Определяет, является ли документированное свойство может иметь значение NULL.  Задайте значение `true` для указания, что свойство может иметь значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementType`  
 Необязательный.  Если `type` имеет значение `Array`, то этот атрибут определяет тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный.  Если `type``Array` и `elementType``Number`, то этот атрибут определяет, является ли элементы массива целые числа.  Установите значение `true`, чтобы указать, что элементы массива целые числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementDomElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `elementType` имеет приоритет над этим атрибутом.  Если `type` имеет значение `Array`, то этот атрибут определяет, является ли элементы массива элементов DOM.  Задайте значение `true` для указания того, что элементы элементов DOM; в противном случае укажите значение `false`.  Если атрибут `elementType` не задан, а параметр `elementDomElement` имеет значение `true`, то IntelliSense обрабатывает каждый элемент массива как `HTMLElement` при выполнении завершение операторов.  
  
 `elementMayBeNull`  
 Необязательный.  Если свойство `type` имеет значение `Array`, указывает ли элементы массива можно задать значение NULL.  Установите значение `true`, чтобы указать, что элементы массива можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `locid`  
 Необязательный.  Идентификатор для данных локализации о свойстве.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в элементе [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Необязательный.  описание свойства.  
  
## Заметки  
 ECMAScript 5 свойств используется элемент [\<summary\>](../ide/summary-javascript.md).  
  
 Используйте элемент `<value>` непосредственно перед объявлением функции `get` или `set`.  
  
## Пример  
 В следующем примере кода показано, как использовать элемент `<value>` для функции `get`.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)