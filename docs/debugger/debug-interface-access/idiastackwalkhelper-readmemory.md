---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory - метод"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Считывает блок данных из образа исполняемого файла в памяти.  
  
## Синтаксис  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Параметры  
 `type`  
 \[in\] значение из [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) перечисление, указывающее тип памяти для чтения.  
  
 va  
 \[in\] виртуальный адрес способом, с которого начинается чтение.  
  
 `cbData`  
 \[in\] размер буфера в байтах.  
  
 `pcbData`  
 \[out\] возвращает число фактически считанных байтов.  If `pbData` существует  `NULL`затем это общее число байтов доступных данных.  
  
 `pbData`  
 \[in, out\] буфер, который заполняется в память при для чтения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)