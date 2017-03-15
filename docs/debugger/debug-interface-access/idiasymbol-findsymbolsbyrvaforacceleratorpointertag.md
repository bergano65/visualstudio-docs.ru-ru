---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Если соответствующее значение тега, этот метод возвращает перечисление символов, содержащихся в этой функции заглушки для заданного относительного виртуальному адресу.  
  
## Синтаксис  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Параметры  
 `tagValue`  
 \[in\] значение тега указателя, для которого pointee записывает символ найден.  
  
 `rva`  
 \[in\] rva, которое используется для фильтрации символов, которые соответствуют переменной pointee с указанным значением тега.  
  
 `ppResult`  
 \[out\] указатель на указатель интерфейса `IDiaEnumSymbols`, который инициализируется с результатом.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## Заметки  
 Этот метод следует вызывать только в интерфейсе `IDiaSymbol`, который соответствует функции заглушки сочетаний клавиш.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)