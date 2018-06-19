---
title: Метод catch (Promise) | Документы Microsoft
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633994"
---
# <a name="catch-method-promise"></a>Метод catch (Promise)
Позволяет указать, какое действие следует выполнить при отклонении объекта Promise.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Параметры  
 `promise`  
 Обязательный. Объект Promise.  
  
 `onRejected`  
 Обязательный. Функция обработчика ошибок, которая будет выполняться при отклонении объекта Promise.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере кода первый вызов функции timeout возвращает значение через 5 000 мс. В данном коде объект Promise отклоняется и выполняется функция обработчика ошибок.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]