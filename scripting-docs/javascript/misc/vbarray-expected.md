---
title: "Ожидался массив VBArray | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-expected"></a>Ожидался массив VBArray
Указанный объект, который не был safeArray Visual Basic, ожидалось только одно.  
  
```  
new VBArray(safeArray);  
```  
  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Аргумент массива safeArray значение VBArray и необходимо получить значение VBArray перед передачей `VBArray` конструктор. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, можно передать только **VBArray** объектов **VBArray** конструктор.  
  
## <a name="see-also"></a>См. также  
 [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)