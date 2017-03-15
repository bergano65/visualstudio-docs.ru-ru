---
title: "IDiaPropertyStorage::Enum | Microsoft Docs"
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
  - "IDiaPropertyStorage::Enum"
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает перечислитель для свойств, входящих в этот набор.  
  
## Синтаксис  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### Параметры  
 `ppenum`  
 \[out\] возвращает `IEnumSTATPROPSTG` объект " \(в пространстве имен Microsoft.VisualStudio.OLE.Interop\), представляющий перечисление свойств.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)