---
title: Функция Unescape (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641404"
---
# <a name="unescape-function-javascript"></a>Функция unescape (JavaScript)
Декодирует `String` закодированы в виде объектов `escape` функции. Не рекомендуется.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `charString` аргумент `String` объекта или литерала для декодирования.  
  
 `unescape` Функция возвращает значение типа string, содержащий содержимое `charstring`. Все символы, кодируемые %*xx* шестнадцатеричной форме заменяются на их эквиваленты набор символов ASCII.  
  
 Символы в кодировке **%u** *xxxx* формат (символов Юникода) заменяются на символ Юникода в шестнадцатеричной кодировке *xxxx*.  
  
> [!NOTE]
>  `unescape` Функция не должна использоваться для декодирования универсальных кодов ресурса (URI). Используйте `decodeURI` и `decodeURIComponent` вместо функции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Функция escape](../../javascript/reference/escape-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)