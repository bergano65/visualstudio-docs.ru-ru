---
title: Ожидался массив VBArray | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064950"
---
# <a name="vbarray-expected"></a>Требуется VBArray
Указанный объект, который не safeArray Visual Basic, когда ожидалось только одно.  
  
```js
new VBArray(safeArray);  
```  
  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Представляет собой значение VBArray аргумента safeArray и необходимо получить значение VBArray перед передачей в `VBArray` конструктор. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, вы передаете только **VBArray** объектов **VBArray** конструктор.  
  
## <a name="see-also"></a>См. также  
 [Объект VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)