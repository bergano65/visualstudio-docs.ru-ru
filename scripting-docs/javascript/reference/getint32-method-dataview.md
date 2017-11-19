---
title: "Метод getInt32 (DataView) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7a985681-ddb1-4c2b-815c-514c17392e82
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae788801a81265d39be5ef090e5820122cbb09b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getint32-method-dataview"></a>Метод getInt32 (DataView)
Получает значение Int32 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения могут быть извлечены из смещения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var testInt = dataView.getInt32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Параметры  
 `testInt`  
 Обязательный. Значение Int32, которое возвращается из метода.  
  
 `byteOffset`  
 Позиция в буфере, с которого следует извлечь значение.  
  
 `littleEndian`  
 Необязательно. Если значение false или не определено, должно быть считано значение с обратным порядком байтов, в противном случае должно быть считано значение с прямым порядком байтов.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они бы чтения за концом представления.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает способ получения первого Int32 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]