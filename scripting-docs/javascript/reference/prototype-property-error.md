---
title: "Свойство prototype (Error) | Документы Microsoft"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-error"></a>Свойство prototype (Error)
Возвращает ссылку на прототип для ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `error` Аргумент является именем ошибку.  
  
 Используйте `prototype` свойство, чтобы предоставить базовый набор функциональных возможностей при возникновении ошибки. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Error`, возвращающий значение самого большого элемента массива, объявите функцию, добавьте ее в `Error.prototype`, а затем используйте его.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты имеют `prototype` свойство, которое доступно только для чтения. Свойства и методы могут быть добавлены в прототип, но объект нельзя назначить другому прототипу. Тем не менее определенных пользователем объектов можно назначить новый прототип.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]