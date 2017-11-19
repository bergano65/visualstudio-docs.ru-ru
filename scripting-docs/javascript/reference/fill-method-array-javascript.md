---
title: "Метод Fill (Array) (JavaScript) | Документы Microsoft"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>Метод fill (Array) (JavaScript)
Заполняет массив указанным значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект массива.  
  
 `value`  
 Обязательный. Значение, используемое для заполнения массива.  
  
 `start`  
 Необязательно. Начальный индекс, используемый для заполнения массива значений. Значение по умолчанию — 0.  
  
 `end`  
 Необязательно. Конечный индекс, используемый для заполнения массива значений. Значением по умолчанию является значение свойства length объекта `this`.  
  
## <a name="remarks"></a>Примечания  
 Если `start` отрицательное, `start` рассматривается как `length` + `start`, где `length` длина массива. Если `end` отрицательное, `end` рассматривается как `length` + `end`.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода массив заполняется значениями:  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]