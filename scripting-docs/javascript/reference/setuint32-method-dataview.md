---
title: "Метод setUint32 (DataView) | Документы Microsoft"
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4d2bf075c46f84c75a174b0ca5954b9cedf154
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setuint32-method-dataview"></a>Метод setUint32 (DataView)
Задает значение Uint32 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения можно задать любой позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Параметры  
 `byteOffset`  
 Позиция в буфере, с которого следует извлечь значение.  
  
 `value`  
 Задаваемое значение.  
  
 `littleEndian`  
 Необязательно. Если значение false или не определено, должны быть написаны с обратным порядком байтов значение, в противном случае значение с прямым порядком байтов должен быть записан.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они записывают за пределами представления.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как задать первый Uint32 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]