---
title: Метод setInt8 (DataView) | Документы Microsoft
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6f9bd9c4b3bea25686036d199d1a987927172d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639494"
---
# <a name="setint8-method-dataview"></a>Метод setInt8 (DataView)
Сохраняет значение Int8 на указанное смещение в байтах от начала представления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## <a name="parameters"></a>Параметры  
 `byteOffset`  
 Позиция в буфере, с которой должно иметь значение.  
  
 `value`  
 Задаваемое значение.  
  
## <a name="remarks"></a>Примечания  
 Эти методы вызывают исключение, если они записывают за пределами представления.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как задать первый Int8 в DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]