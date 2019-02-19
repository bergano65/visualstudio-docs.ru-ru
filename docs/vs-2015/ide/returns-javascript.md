---
title: '&lt;Возвращает&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54801780"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Возвращает&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации для результата вызова функции или метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 Необязательный параметр. Тип данных возвращаемого значения. Тип может принимать одно из следующих значений:  
  
- Это язык на ECMAScript введите спецификацией ECMAScript 5, например `Number` и `Object`.  
  
- Объект DOM, таких как `HTMLElement`, `Window`, и `Document`.  
  
- Функция конструктора, JavaScript.  
  
  `integer`  
  Необязательный параметр. Если `type` является `Number`, указывает, является ли возвращаемое значение является целым числом. Значение `true` , возвращаемое значение является целое число; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `domElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `type` атрибут имеет приоритет над этот атрибут. Этот атрибут указывает, является ли значение документированных элемент DOM. Значение `true` для указания, что возвращаемое значение является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense рассматривает документированных возвращаемое значение как `HTMLElement` при выполнении завершения операторов.  
  
  `mayBeNull`  
  Необязательный параметр. Указывает, они возвращают ли значение может быть задано значение null. Значение `true` чтобы указать, что возвращаемое значение может быть задано в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementType`  
  Необязательный параметр. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
  `elementInteger`  
  Необязательный параметр. Если `type` — `Array` и `elementType` является `Number`, этот атрибут указывает, являются ли элементы в массив целых чисел. Значение `true` для указания, представляют собой целые числа элементов в массиве; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementDomElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `elementType` атрибут имеет приоритет над этот атрибут. Если `type` является `Array`, этот атрибут указывает, являются ли элементы в массиве элементов DOM. Значение `true` для указания, элементы являются элементами DOM; в противном случае — значение `false`. Если `elementType` атрибут не задан и `elementDomElement` присваивается `true`, IntelliSense обрабатывает каждый элемент массива в виде `HTMLElement` при выполнении завершения операторов.  
  
  `elementMayBeNull`  
  Необязательный параметр. Если `type` является `Array`, указывает ли элементы в массиве можно задать значение null. Значение `true` чтобы указать, что элементы в массиве может быть установлен в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `locid`  
  Необязательный параметр. Идентификатор для локализации сведения о возвращаемом значении. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) тега.  
  
  `value`  
  Необязательный параметр. Указывает код, который должен вычисляться для использования с IntelliSense вместо код самой функции. Например, можно использовать этот атрибут предоставляет IntelliSense для асинхронных обратных вызовах, такие как `Promise`. С помощью `value` атрибут `<returns>` элемент может повысить производительность IntelliSense, игнорируя выполнение написания длинного кода.  
  
  `description`  
  Необязательный параметр. Описание возвращаемого значения.  
  
## <a name="remarks"></a>Примечания  
 `<returns>` Элемент должен быть помещен в тело функции до всех операторов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `<returns>` элемент.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
