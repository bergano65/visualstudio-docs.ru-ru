---
title: Свойство constructor (String) | Документы Microsoft
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636064"
---
# <a name="constructor-property-string"></a>Свойство constructor (String)
Указывает функцию, которая создает строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `string` имя строки.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда входят все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов, за исключением `Global` и `Math` объектов. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование свойства конструктора.  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]