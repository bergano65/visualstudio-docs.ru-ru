---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::pdataByVA - метод"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает фрагмент данных PDATA, связанный с виртуальным адресом.  
  
## Синтаксис  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Параметры  
 `va`  
 \[in\] определяет виртуальный адрес данных для получения.  
  
 `cbData`  
 \[in\] размер в байтах, который требуется получить.  
  
 `pcbData`  
 \[out\] возвращает фактический размер в байтах, которые были получены.  
  
 `pbData`  
 \[in, out\] буфер, который заполняется с данными.  Не может иметь значение `NULL`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если PDATA для указанного адреса.  В противном случае возвращает код ошибки.  
  
## Заметки  
 PDATA \(раздел .pdata с именем ""\) compiland содержит сведения об обработке ошибок для функций.  
  
 Вызывающий объект известно, сколько данных должен быть возвращен поэтому вызывающий не имеет никакой необходимости запросить объем данных.  Поэтому приемлемо для реализации этого метода возвращать ошибку, если `pbData` параметр  `NULL`.  
  
## См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)