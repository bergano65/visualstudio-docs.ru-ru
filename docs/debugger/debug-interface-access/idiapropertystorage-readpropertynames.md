---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Имена извлечение соответствующей строки для заданного идентификатора свойства.  
  
## Синтаксис  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Параметры  
 `cpropid`  
 \[in\] количество идентификаторов свойства in `rgpropid`.  
  
 `rgpropid`  
 \[in\] массив идентификаторов свойства, для которых, чтобы получить имена \(`PROPID` определяет, а в WTypes.h  `ULONG`\).  
  
 `rglpwstrName`  
 \[in, out\] массив имен свойств для идентификаторов указанного свойства.  Массив должен pre\-выделить для хранения количества запрошенных имен свойств и должен содержать хотя бы `cpropid``BSTR` строки.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Возвращаемые имена свойств необходимо освободить \(путем вызова `SysFreeString` функция\), если они больше не требуются.  
  
## См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)