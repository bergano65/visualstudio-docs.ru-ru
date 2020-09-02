---
title: '&lt;summary&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646848"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает описание для функции или метода.

## <a name="syntax"></a>Синтаксис

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Параметры
 `locid` Необязательный. Идентификатор для сведений о локализации для функции или метода. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в [\<loc>](../ide/loc-javascript.md) элементе.

 `description` Необязательный. Описание функции или метода.

## <a name="remarks"></a>Remarks
 Элементы, используемые для комментирования функций, в том числе [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) и [\<returns>](../ide/returns-javascript.md) , должны быть помещены в тело функции перед любыми инструкциями.

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется использование элемента `<summary>`.

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

## <a name="see-also"></a>См. также:
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
