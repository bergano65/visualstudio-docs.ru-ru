---
title: "Метод moveFirst (Enumerator) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: moveFirst
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: MoveFirst method
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8c59194a5655730e8509b43533f699aeef51d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="movefirst-method-enumerator-javascript"></a>Метод moveFirst (Enumerator) (JavaScript)
Сбрасывает текущий элемент в коллекции к первому элементу.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
enumObj.moveFirst( )   
```  
  
## <a name="remarks"></a>Примечания  
 Обязательная ссылка *enumObj* представляет собой любой объект `Enumerator` .  
  
 Если в коллекции нет элементов, текущий элемент получает значение undefined (не определен).  
  
## <a name="example"></a>Пример  
 В следующем примере метод `moveFirst` используется для вычисления элементов коллекции `Drives` с начала списка.  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод atEnd (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Метод Item (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Метод moveNext (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)