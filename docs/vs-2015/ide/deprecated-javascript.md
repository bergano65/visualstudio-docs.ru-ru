---
title: '&gt; &lt;deprecated (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665808"
---
# <a name="ltdeprecatedgt-javascript"></a>&gt; &lt;deprecated (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает устаревшую функцию или метод.

## <a name="syntax"></a>Синтаксис

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Параметры
 `type` Необязательный. Указывает, будет ли удалена функция или метод в будущем выпуске или же функция или метод уже удалена и их использование может привести к ошибке. Задайте значение `deprecate`, чтобы указать, что функция или метод будут удалены в следующем выпуске. Задайте значение `remove`, чтобы указать, что функция или метод уже были удалены.

 `locid` Необязательный. Идентификатор для сведений о локализации для функции или метода. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в элементе [\<loc>](../ide/loc-javascript.md).

 `description` Необязательный. Описание функции или метода, которое является устаревшим.

## <a name="remarks"></a>Примечания
 Элементы, используемые для комментирования функций, которые включают `<deprecated>`, должны быть помещены в тело функции перед любыми инструкциями. Если функция помечается как устаревшая, рекомендуется заменить элемент [\<summary >](../ide/summary-javascript.md) элементом `<deprecated>`.

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется использование элемента `<deprecated>`.

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

## <a name="see-also"></a>См. также
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
