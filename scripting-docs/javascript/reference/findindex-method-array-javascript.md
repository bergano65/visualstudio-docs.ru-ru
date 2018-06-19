---
title: Метод findIndex (Array) (JavaScript) | Документы Microsoft
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636584"
---
# <a name="findindex-method-array-javascript"></a>Метод findIndex (Array) (JavaScript)
Возвращает значение индекса для первого элемента массива, который соответствует тестовым критериям, указанным в функции обратного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект массива.  
  
 `callbackfn`  
 Обязательный. Функция обратного вызова, тестирующая каждый элемент массива.  
  
 `thisArg`  
 Необязательно. Определяет объект `this` в функции обратного вызова. Если он не указан, объект `this` остается неопределенным.  
  
## <a name="remarks"></a>Примечания  
 `findIndex` однократно вызывает функцию обратного вызова для каждого элемента в массиве в порядке возрастания, пока какой-либо элемент не вернет значение `true`. Как только какой-либо элемент вернет значение true, `findIndex` возвращает значение индекса элемента, который выдал это значение. Если ни один элемент в массиве не возвращает значение true, `findIndex` возвращает значение –1.  
  
 `findIndex` не изменяет объект массива.  
  
## <a name="callback-function-syntax"></a>Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, index, thisArg)`  
  
 При объявлении функции обратного вызова можно использовать до трех параметров.  
  
 Функция обратного вызова имеет следующие параметры.  
  
|Аргумент обратного вызова|Определение|  
|-----------------------|----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`arrayObj`|Перебираемый объект массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере функция обратного вызова проверяет, равно ли значение каждого элемента массива двум.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере для проверки каждого элемента используется синтаксис стрелок. В данном примере ни один из элементов не выдает значение `true`, так что `findIndex` возвращает –1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]