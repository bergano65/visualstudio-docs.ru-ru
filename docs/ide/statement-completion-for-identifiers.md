---
title: "Завершение операторов с использованием идентификаторов | Microsoft Docs"
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
  - "IntelliSense [JavaScript], завершение операторов"
  - "завершение операторов, IntelliSense для JavaScript"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Завершение операторов с использованием идентификаторов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript не допускает явного ввода для объявления переменных.  В результате IntelliSense не всегда может предоставить списки завершения для объектов.  Это может произойти в различных ситуациях.  Ниже приведены несколько распространенных.  
  
-   Параметр объявлен, но он не был вызван где\-либо в активном документе, как показано в следующем примере.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Объект находится в функции, которая вызывается в ответ на событие.  Во время разработки ядра IntelliSense не удается определить тип объектов, используемых в данной ситуации.  
  
     Если ядро IntelliSense можно определить, что события должен быть вызван, обычно через использование `addEventListener` для события в активном документе, предоставляется более точные сведения о IntelliSense.  
  
 Когда не удается определить объект IntelliSense модуль IntelliSense заполняет список завершения с именованные сущности или идентификаторов, которые присутствуют в активном документе.  Когда список завершения содержит эти идентификаторы, сведения значки появляются рядом с ними.  Кроме того всплывающей подсказки для каждого идентификатора указывает, что выражение неизвестно.  На следующем рисунке показана инструкция параметры завершения для объекта типа `light` , не может быть определен, так как объект и его свойства не определены.  Тем не менее `intensity` свойство доступно в списке идентификатор, так как он используется в `illuminate` функции.  
  
 **Параметры завершения для объекта, который не может быть определен**  
  
 ![Технология IntelliSense для идентификаторов JavaScript](~/docs/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 Список завершения объекта можно переопределить при помощи комментариев XML\-документации или возможности расширения JavaScript IntelliSense.  Используя эти средства, можно предоставить сведения о типе и более описательные сведения о IntelliSense при его в противном случае оказаться недоступны.  Дополнительные сведения см. в разделах [Расширение IntelliSense для JavaScript](../ide/extending-javascript-intellisense.md) и [Практическое руководство. Создание комментариев XML\-документации для JavaScript](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## См. также  
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)