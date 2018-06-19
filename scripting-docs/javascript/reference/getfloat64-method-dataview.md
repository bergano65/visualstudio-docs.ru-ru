---
title: Метод getFloat64 (DataView) | Документы Microsoft
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
ms.assetid: 347adeb6-b24c-4e7d-8b6b-8e36aacdcae1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab6d52fcaa82cc957ba47b5ef2acdfbef90152d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636464"
---
# <a name="getfloat64-method-dataview"></a>Метод getFloat64 (DataView)
Получает значение Float64 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения могут быть извлечены из смещения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var testFloat = dataView.getFloat64(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Параметры  
 `testFloat`  
 Обязательный. Значение Float64, которое возвращается из метода.  
  
 `byteOffset`  
 Позиция в буфере, с которого следует извлечь значение.  
  
 `littleEndian`  
 Необязательно. Если значение false или не определено, должно быть считано значение с обратным порядком байтов, в противном случае должно быть считано значение с прямым порядком байтов.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они бы чтения за концом представления.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает способ получения первого Float64 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat64(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]