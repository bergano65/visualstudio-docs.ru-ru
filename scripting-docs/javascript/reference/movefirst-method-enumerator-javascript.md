---
title: "Метод moveFirst (Enumerator) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "moveFirst"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "MoveFirst - метод"
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод moveFirst (Enumerator) (JavaScript)
Сбрасывает текущий элемент в коллекции к первому элементу.  
  
> [!WARNING]
>  Этот объект поддерживается только в Internet Explorer.  
  
## Синтаксис  
  
```  
  
enumObj.moveFirst( )  
```  
  
## Заметки  
 Обязательная ссылка *enumObj* представляет собой любой объект `Enumerator`.  
  
 Если в коллекции нет элементов, текущий элемент получает значение undefined \(не определен\).  
  
## Пример  
 В следующем примере метод `moveFirst` используется для вычисления элементов коллекции `Drives` с начала списка.  
  
```javascript  
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
  
## Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)  
  
## См. также  
 [Метод atEnd \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Метод item \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Метод moveNext \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)