---
title: "Объект Enumerator (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Объект Enumerator (JavaScript)
Обеспечивает перечисление элементов в коллекции.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer, но не в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Параметры  
 `enumObj`  
 Обязательный. Имя переменной, которой присваивается объект `Enumerator` .  
  
 `collection`  
 Необязательный. Любой объект Collection.  
  
## <a name="remarks"></a>Примечания  
 Коллекции отличаются от массивов тем, что элементы коллекции недоступны напрямую. Вместо использования индексов, как это делается в массивах, можно перемещать указатель текущего элемента только в первый или в следующий элемент коллекции.  
  
 Объект `Enumerator` предоставляет способ доступа к любому элементу коллекции и работает аналогично инструкции `For...Each` в VBScript.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано применение объекта `Enumerator` .  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Свойства  
 Объект `Enumerator` не имеет свойств.  
  
## <a name="methods"></a>Методы  
 [Метод atEnd](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [метод item](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [метод moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [метод moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>См. также  
 [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)