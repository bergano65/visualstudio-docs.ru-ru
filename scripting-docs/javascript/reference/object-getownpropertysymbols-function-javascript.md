---
title: "Функция Object.getOwnPropertySymbols (JavaScript) | Документы Microsoft"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Функция Object.getOwnPropertySymbols (JavaScript)
Возвращает собственные символьные свойства объекта. Собственные символьные свойства объекта — это свойства, которые определяются в самом объекте, а не наследуются им от прототипа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, содержащий собственные символы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив, содержащий собственные символы объекта.  
  
## <a name="remarks"></a>Примечания  
 Для получения символьных свойств объекта используйте функцию `Object.getOwnPropertySymbols`. Функция `Object.getOwnPropertyNames` не возвращает символьные свойства.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как получить символьные свойства объекта.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]