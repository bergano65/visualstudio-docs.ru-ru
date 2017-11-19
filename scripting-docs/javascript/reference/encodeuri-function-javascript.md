---
title: "Функция encodeURI (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>Функция encodeURI (JavaScript)
Кодирует текстовую строку как допустимый универсальный идентификатор ресурса (URI)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `URIString` аргумент имеет значение, представляющее закодированный URI.  
  
 `encodeURI` Функция возвращает закодированный URI. Если передать результат в `decodeURI`, возвращается исходная строка. `encodeURI` Функция не кодирует следующие символы: «:», «/», «;», и «?». Используйте `encodeURIComponent` кодировать эти символы.  
  
## <a name="example"></a>Пример  
 Следующий код сначала кодирует и декодирует URI затем.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)