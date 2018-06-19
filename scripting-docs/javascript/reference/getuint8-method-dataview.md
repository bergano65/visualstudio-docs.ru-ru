---
title: Метод getUint8 (DataView) | Документы Microsoft
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 315baa2ca5abfe006a7f8d524619479d99a11fc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636744"
---
# <a name="getuint8-method-dataview"></a>Метод getUint8 (DataView)
Получает значение Uint8 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения могут быть извлечены из смещения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## <a name="parameters"></a>Параметры  
 `testInt`  
 Обязательный. Значение Uint8, которое возвращается из метода.  
  
 `byteOffset`  
 Позиция в буфере, с которого следует извлечь значение.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они бы чтения за концом представления.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает способ получения первого Uint8 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]