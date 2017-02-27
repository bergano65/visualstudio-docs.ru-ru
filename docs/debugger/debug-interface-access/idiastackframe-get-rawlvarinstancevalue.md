---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_rawLVarInstanceValue - метод"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Этот метод получает значение заданной локальной переменной в виде необработанных байт.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Параметры  
 `pInstance`  
 \[in\] `IDiaLVarInstance` объект, представляющий экземпляр локальной переменной для получения значения.  
  
 `cbDataMax`  
 \[in\] максимальное число байт в буфере указало к которым следуют `pbData`.  Это может превышать 8 байт \(`sizeof(ULONGLONG)`\).  
  
 `pcbData`  
 \[out\] возвращает фактическое число байтов, хранимых в буфере.  
  
 `pbData`  
 \[out\] буфер, который необходимо заполнить данными.  Он не может иметь значение `NULL`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)