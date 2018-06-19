---
title: Метод setInt32 (DataView) | Документы Microsoft
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
ms.assetid: 07e5f068-0e3f-4c23-84b3-c72658d7f194
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00f3f6b03cdd3a8d5d7b95184f1c0ff5c356592a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639134"
---
# <a name="setint32-method-dataview"></a>Метод setInt32 (DataView)
Задает значение Int32 на указанное смещение в байтах от начала представления. Не имеет ограничений выравнивания; многобайтовую значения можно задать любой позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dataView.setInt32 (byteOffset, value, littleEndian);   
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
 Приведенный ниже показано, как задать первый Int32 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]