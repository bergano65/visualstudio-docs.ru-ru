---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
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
  - "summary - XML-тег JavaScript"
  - "XML-тег JavaScript <summary>"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает описание функции или метода.  
  
## Синтаксис  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Параметры  
 `locid`  
 Необязательный.  Идентификатор для данных о локализации функции или метода.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в элементе [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Необязательный.  Описание функции или метода.  
  
## Заметки  
 Элементы, используемые для создания заметок к функции, включая [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) и [\<returns\>](../ide/returns-javascript.md), должен быть помещен в теле функции перед всеми выписками.  
  
## Пример  
 В следующем коде показано, как использовать элемент `<summary>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)