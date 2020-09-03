---
title: Завершение операторов для идентификаторов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643858"
---
# <a name="statement-completion-for-identifiers"></a>Завершение операторов с использованием идентификаторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript не допускает явную типизацию для объявлений переменных. В результате IntelliSense не всегда может предоставлять списки завершения для объектов. Это может произойти в различных ситуациях. Ниже приведены некоторые распространенные из них.

- Параметр объявляется, но не вызывается в других местах активного документа, как показано в следующем примере.

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

- Объект находится в функции, которая вызывается в ответ на событие. Во время разработки механизм IntelliSense не может определить тип объектов, используемых в этой ситуации.

   Если подсистема IntelliSense может определить, что событие должно вызываться, как правило, с помощью `addEventListener` для события в активном документе, предоставляется более точная информация об IntelliSense.

  Если технология IntelliSense не может опознать объект, обработчик IntelliSense заполняет список завершения именованными сущностями или идентификаторами, присутствующими в активном документе. Если список завершения содержит эти идентификаторы, рядом с ними отображаются значки сведений. Кроме того, подсказка для каждого идентификатора указывает на то, что выражение неизвестно. На следующем рисунке показаны параметры завершения инструкции для объекта типа `light` , который не может быть идентифицирован, так как объект и его свойства не определены. Однако `intensity` свойство доступно в списке идентификаторов, так как оно было использовано в `illuminate` функции.

  **Параметры завершения для объекта, который не может быть идентифицирован**

  ![Технология IntelliSense для идентификаторов JavaScript](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  Можно переопределить список завершения для объекта с помощью комментариев XML-документации или функций расширяемости IntelliSense JavaScript. Используя эти функции, можно предоставить сведения о типах и более описательные сведения IntelliSense, если они могут быть недоступны другим способом. Дополнительные сведения см. в статьях [расширение IntelliSense для JavaScript](../ide/extending-javascript-intellisense.md) и [Создание комментариев XML-документации](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>См. также:
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)
