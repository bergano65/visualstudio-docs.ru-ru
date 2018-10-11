---
title: Завершение операторов для идентификаторов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 630d0f55792b06cd1c99f9c1947a5ae73bce2683
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881037"
---
# <a name="statement-completion-for-identifiers"></a>Завершение операторов с использованием идентификаторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [документация по Visual Studio 2017](/visualstudio/).  
  
JavaScript не допускает явной типизации для объявления переменных. Таким образом IntelliSense не всегда может предоставить список завершения для объектов. Это может произойти в различных ситуациях. Ниже приведены несколько распространенных рисков.  
  
-   Параметр объявлен, но он не был вызван в другом месте в активном документе, как показано в следующем примере.  
  
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
  
-   Объект находится в функцию, которая вызывается в ответ на событие. Во время разработки обработчик IntelliSense не удается определить тип объектов, используемых в этой ситуации.  
  
     Если обработчик IntelliSense может определить, что событие должно вызываться, обычно путем использования `addEventListener` для события в активном документе, предоставляется более точные сведения IntelliSense.  
  
 Если технология IntelliSense не удалось определить объект, обработчик IntelliSense заполняет список завершения с помощью именованных сущностей или идентификаторы, которые присутствуют в активном документе. Если список завершения содержит эти идентификаторы, рядом с ними отображаются значки сведения. Кроме того в подсказке для каждого идентификатора указывает, что выражение неизвестно. На следующем рисунке показана инструкция параметры завершения для объекта типа `light` , не может быть определен, так как объект и его свойства не определены. Тем не менее `intensity` свойство доступно в список идентификаторов, так как он используется в `illuminate` функции.  
  
 **Параметры завершения для объекта, который не может быть определен**  
  
 ![IntelliSense для JavaScript для идентификаторов](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
 Список завершения для объекта можно переопределить с помощью комментариев XML-документации и расширяемостью IntelliSense для JavaScript. Используя эти функции, можно предоставить сведения о типе и дополнительные описательные сведения IntelliSense при его в противном случае недоступен. Дополнительные сведения см. в разделе [расширение IntelliSense для JavaScript](../ide/extending-javascript-intellisense.md) и [создавать комментарии XML-документации](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>См. также  
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)



