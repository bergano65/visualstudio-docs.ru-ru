---
title: '&lt;значение&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799146"
---
# <a name="ltvaluegt-javascript"></a>&lt;значение&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации для `get` и `set` функции для свойства ECMAScript 3.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 Необязательный параметр. Тип данных свойства. Тип может принимать одно из следующих значений:  
  
- Тип языка ECMAScript, заключается в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
- Объект DOM, таких как `HTMLElement`, `Window`, и `Document`.  
  
- Функция конструктора, JavaScript.  
  
  `integer`  
  Необязательный параметр. Если `type` является `Number`, указывающее, является ли свойство целое число. Значение `true` для указания, что свойство является целое число; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `domElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `type` атрибут имеет приоритет над этот атрибут. Этот атрибут указывает, является ли свойство документированных DOM-элемента. Значение `true` для указания, что свойство является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense рассматривает документированных свойство как `HTMLElement` при выполнении завершения операторов.  
  
  `mayBeNull`  
  Необязательный параметр. Указывает, можно ли задать свойство документированных в значение null. Значение `true` чтобы указать, что свойство может быть задано в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementType`  
  Необязательный параметр. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
  `elementInteger`  
  Необязательный параметр. Если `type` — `Array` и `elementType` является `Number`, этот атрибут указывает, являются ли элементы в массив целых чисел. Значение `true` для указания, представляют собой целые числа элементов в массиве; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementDomElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `elementType` атрибут имеет приоритет над этот атрибут. Если `type` является `Array`, этот атрибут указывает, являются ли элементы в массиве элементов DOM. Значение `true` для указания, элементы являются элементами DOM; в противном случае — значение `false`. Если `elementType` атрибут не задан и `elementDomElement` присваивается `true`, IntelliSense обрабатывает каждый элемент массива в виде `HTMLElement` при выполнении завершения операторов.  
  
  `elementMayBeNull`  
  Необязательный параметр. Если `type` является `Array`, указывает ли элементы в массиве можно задать значение null. Значение `true` чтобы указать, что элементы в массиве может быть установлен в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `locid`  
  Необязательный параметр. Идентификатор для локализации сведения о свойстве. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) элемент.  
  
  `description`  
  Необязательный параметр. Описание свойства.  
  
## <a name="remarks"></a>Примечания  
 Используйте свойства ECMAScript 5 [ \<summary >](../ide/summary-javascript.md) элемент.  
  
 Используйте `<value>` элемент непосредственно перед `get` или `set` функции.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `<value>` элемент на `get` функции.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
