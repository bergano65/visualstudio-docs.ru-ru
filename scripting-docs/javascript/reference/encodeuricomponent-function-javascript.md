---
title: Функция encodeURIComponent (JavaScript) | Документы Microsoft
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636434"
---
# <a name="encodeuricomponent-function-javascript"></a>Функция encodeURIComponent (JavaScript)
Кодирует текстовую строку как допустимый универсальный код ресурса (URI) компонент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `encodedURIString` аргумент имеет значение, представляющее закодированный компонент URI.  
  
 `encodeURIComponent` Функция возвращает закодированный URI. Если передать результат в `decodeURIComponent`, возвращается исходная строка. Поскольку `encodeURIComponent` функция кодирует все символы, будьте внимательны, если строка представляет путь, например **/folder1/folder2/default.html**. Символы косой черты кодируется и не будет допустимым, если при передаче запроса на веб-сервере. Используйте `encodeURI` функционировать, если строка содержит несколько компонентов URI.  
  
## <a name="example"></a>Пример  
 В следующем коде сначала кодирует компонента URI и затем расшифровывает его.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)