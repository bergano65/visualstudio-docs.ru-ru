---
title: '&lt;Возвращает&gt; (JavaScript) | Документация Майкрософт'
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
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 733fa3706eb7c8eeef6a8e8243eaeeac6d1b0f78
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879738"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Возвращает&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [документация по Visual Studio 2017](/visualstudio/).  
  
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
 Необязательный. Тип данных возвращаемого значения. Тип может принимать одно из следующих значений:  
  
-   Это язык на ECMAScript введите спецификацией ECMAScript 5, например `Number` и `Object`.  
  
-   Объект DOM, таких как `HTMLElement`, `Window`, и `Document`.  
  
-   Функция конструктора, JavaScript.  
  
 `integer`  
 Необязательный. Если `type` является `Number`, указывает, является ли возвращаемое значение является целым числом. Значение `true` , возвращаемое значение является целое число; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `domElement`  
 Необязательный. Этот атрибут является устаревшим; `type` атрибут имеет приоритет над этот атрибут. Этот атрибут указывает, является ли значение документированных элемент DOM. Значение `true` для указания, что возвращаемое значение является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense рассматривает документированных возвращаемое значение как `HTMLElement` при выполнении завершения операторов.  
  
 `mayBeNull`  
 Необязательный. Указывает, они возвращают ли значение может быть задано значение null. Значение `true` чтобы указать, что возвращаемое значение может быть задано в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `elementType`  
 Необязательный. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный. Если `type` — `Array` и `elementType` является `Number`, этот атрибут указывает, являются ли элементы в массив целых чисел. Значение `true` для указания, представляют собой целые числа элементов в массиве; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `elementDomElement`  
 Необязательный. Этот атрибут является устаревшим; `elementType` атрибут имеет приоритет над этот атрибут. Если `type` является `Array`, этот атрибут указывает, являются ли элементы в массиве элементов DOM. Значение `true` для указания, элементы являются элементами DOM; в противном случае — значение `false`. Если `elementType` атрибут не задан и `elementDomElement` присваивается `true`, IntelliSense обрабатывает каждый элемент массива в виде `HTMLElement` при выполнении завершения операторов.  
  
 `elementMayBeNull`  
 Необязательный. Если `type` является `Array`, указывает ли элементы в массиве можно задать значение null. Значение `true` чтобы указать, что элементы в массиве может быть установлен в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `locid`  
 Необязательный. Идентификатор для локализации сведения о возвращаемом значении. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) тега.  
  
 `value`  
 Необязательный. Указывает код, который должен вычисляться для использования с IntelliSense вместо код самой функции. Например, можно использовать этот атрибут предоставляет IntelliSense для асинхронных обратных вызовах, такие как `Promise`. С помощью `value` атрибут `<returns>` элемент может повысить производительность IntelliSense, игнорируя выполнение написания длинного кода.  
  
 `description`  
 Необязательный. Описание возвращаемого значения.  
  
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
  
## <a name="see-also"></a>См. также  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)



