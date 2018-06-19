---
title: Функция decodeURI (JavaScript) | Документы Microsoft
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
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636244"
---
# <a name="decodeuri-function-javascript"></a>Функция decodeURI (JavaScript)
Возвращает декодированную версию из кодировке универсального ресурса (URI).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `URIstring` аргумент имеет значение, представляющее закодированный URI.  
  
 Используйте `decodeURI` функции вместо устаревших `unescape` функции.  
  
 `decodeURI` Функция возвращает значение типа string.  
  
 Если `URIString` является недопустимым, возникает исключение URIError.  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Пример  
 В следующем коде сначала кодирует компонента URI и затем расшифровывает его.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Объект Global](../../javascript/reference/global-object-javascript.md)