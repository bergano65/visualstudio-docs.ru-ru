---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет нерекомендуемые функции или метода.  
  
## Синтаксис  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Параметры  
 `type`  
 Необязательный.  Определяет, будут ли удалены функции или метода в будущем выпуске, или удалены ли функция или метод, и что его использование может привести к ошибке.  Задайте значение `deprecate` для указания того, что функция или метод будут удалены в будущих выпусках.  Задайте значение `remove` для указания того, что функция или метод уже были удалены.  
  
 `locid`  
 Необязательный.  Идентификатор для данных о локализации функции или метода.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в элементе [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Необязательный.  Описание функций или методов, для перевода.  
  
## Заметки  
 Элементы, используемые для создания заметок к функции, включая `<deprecated>`, должен быть помещен в теле функции перед всеми выписками.  Когда помечается как функции стали сопоставления, рекомендуется заменить его элемент [\<summary\>](../ide/summary-javascript.md) с элементом `<deprecated>`.  
  
## Пример  
 В следующем коде показано, как использовать элемент `<deprecated>`.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)