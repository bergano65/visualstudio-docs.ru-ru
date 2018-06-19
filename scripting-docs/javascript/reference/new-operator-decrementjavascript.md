---
title: Оператор New (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638584"
---
# <a name="new-operator-javascript"></a>Оператор new (JavaScript)
Создает новый объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Параметры  
 `constructor`  
 Обязательный. Конструктор объекта. Скобки можно опустить, если конструктор не принимает аргументы.  
  
 `arguments`  
 Необязательно. Аргументы можно передать конструктору нового объекта.  
  
## <a name="remarks"></a>Примечания  
 `new` Оператор выполняет следующие задачи:  
  
-   Он создает объект без членов.  
  
-   Он вызывает конструктор для этого объекта, передавая указатель на вновь созданный объект как `this` указатель.  
  
-   Затем конструктор инициализирует объект в соответствии с аргументы, переданные в конструктор.  
  
 Ниже приведены примеры допустимых вариантов **новый** оператор.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)