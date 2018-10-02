---
title: '&lt;Сводка&gt; (JavaScript) | Документация Майкрософт'
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
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79aeb36e62279dcdafd2adb0143fa70ce2ee0eba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569204"
---
# <a name="ltsummarygt-javascript"></a>&lt;Сводка&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [документация по Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Указывает описание для функции или метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>Параметры  
 `locid`  
 Необязательный. Идентификатор для локализации сведения о функции или метода. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) элемент.  
  
 `description`  
 Необязательный. Описание функции или метода.  
  
## <a name="remarks"></a>Примечания  
 Элементы, используемые для добавления заметок к функции, которые включают [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), и [ \<возвращает >](../ide/returns-javascript.md), должен быть помещен в тело функции до всех операторов.  
  
## <a name="example"></a>Пример  
 Ниже показано, как использовать `<summary>` элемент.  
  
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
  
## <a name="see-also"></a>См. также  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)



