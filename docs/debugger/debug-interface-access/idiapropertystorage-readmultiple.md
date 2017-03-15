---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Читает указанные свойства из текущего набора свойств.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Параметры  
 `cpspec`  
 \[in\] количество свойств, указанных в `rgpspec` массив.  Если значение равно нулю, метод не возвращает никаких свойств, но возвращает `S_OK` как код успешного завершения.  
  
 `rgpspec`  
 \[in\] массив свойств, который нужно считать.  Свойства могут быть указаны идентификатор свойства или необязательным именем строки.  Нет необходимости указывать свойства в каком\-либо определенном порядке в массиве.  Массив может содержать повторяющиеся свойства, в результате чего повторяющихся значений свойств при возврате для простых свойств.  Свойства Non\-простоя должны возвращать доступ запрещен в попытке открыть их во второй раз.  Массив может содержать смесь идентификаторы свойств и идентификаторы строк.  Этот массив должен содержать хотя бы `cpspec` количество значений свойств.  
  
 `rgvar`  
 \[in, out\] массив `PROPVARIANT` структуры \(в пространстве имен Microsoft.VisualStudio.OLE.Interop\) для заполнения со значениями для каждого свойства.  Массив должен иметь хотя бы `cpspec` элементы в размере.  Вызывающему объекту не требуется инициализации значений в массиве.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если одно или несколько свойств не найдены.  в противном случае возвращает код ошибки.  
  
## Заметки  
 Если свойство не было найдено, соответствующей записи в `rgvar` \- a  `VARIANT` с типом   `VT_EMPTY`.  
  
## См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)