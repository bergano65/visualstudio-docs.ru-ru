---
title: '&lt;Рекомендуется использовать&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759760"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;Рекомендуется использовать&gt; (JavaScript)
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
 `type`  
 Необязательный параметр. Указывает ли функция или метод будет поддерживаться в будущем выпуске или ли функция или метод уже был удален, и что его использование может привести к ошибке. Значение `deprecate` для указания, что функция или метод будет удален в будущем выпуске. Значение `remove` для указания, что функция или метод уже был удален.  
  
 `locid`  
 Необязательный параметр. Идентификатор для локализации сведения о функции или метода. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) элемент.  
  
 `description`  
 Необязательный параметр. Описание функции или метода, которая поддерживается.  
  
## <a name="remarks"></a>Примечания  
 Элементы, используемые для добавления заметок к функции, которые включают `<deprecated>`, необходимо поместить в тело функции до всех операторов. Когда функция помечается как нерекомендуемые, мы советуем заменить его [ \<summary >](../ide/summary-javascript.md) элемент с `<deprecated>` элемент.  
  
## <a name="example"></a>Пример  
 Ниже показано, как использовать `<deprecated>` элемент.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
