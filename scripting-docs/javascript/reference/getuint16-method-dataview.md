---
title: Метод getUint16 (DataView) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3c0d9ad8-30b0-42a3-b0fe-aa805398c396
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2da1ea7bdbbbc1d99f9b7b6c33e4b3d83e0ba84f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636674"
---
# <a name="getuint16-method-dataview"></a>Метод getUint16 (DataView)
Получает значение Uint16 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения могут быть извлечены из смещения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var testInt = dataView.getUint16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Параметры  
 `testInt`  
 Обязательный. Значение Uint16, которое возвращается из метода.  
  
 `byteOffset`  
 Позиция в буфере, с которого следует извлечь значение.  
  
 `littleEndian`  
 Необязательно. Если значение false или не определено, должно быть считано значение с обратным порядком байтов, в противном случае должно быть считано значение с прямым порядком байтов.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они бы чтения за концом представления.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает способ получения первого Uint16 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]