---
title: Метод moveNext (Enumerator) (JavaScript) | Документы Microsoft
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
- moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639774"
---
# <a name="movenext-method-enumerator-javascript"></a>Метод moveNext (Enumerator) (JavaScript)
Перемещает текущий элемент к следующему элементу в коллекции.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>Примечания  
 Обязательная ссылка *enumObj* представляет собой любой объект `Enumerator` .  
  
 Если перечислитель находится в конце коллекции или коллекция пуста, текущий элемент получает значение undefined (не определен).  
  
## <a name="example"></a>Пример  
 В следующем примере метод **moveNext** используется для перемещения к следующему диску в коллекции `Drives` .  
  
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
 [Метод moveFirst (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)