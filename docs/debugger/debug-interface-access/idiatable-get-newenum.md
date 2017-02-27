---
title: "IDiaTable::get__NewEnum | Microsoft Docs"
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
  - "IDiaTable::get__NewEnum - метод"
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaTable::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версия данного перечислителя.  
  
## Синтаксис  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `IUnknown` интерфейс, представляющий  <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версия данного перечислителя.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)