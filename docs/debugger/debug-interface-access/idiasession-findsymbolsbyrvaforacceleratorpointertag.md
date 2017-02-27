---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Если соответствующее значение тега, этот метод возвращает перечисление символов, содержащихся в заданной родительской функции заглушки сочетаний клавиш в указанном относительного виртуальному адресу.  
  
## Синтаксис  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Параметры  
 `parent`  
 \[in\] `IDiaSymbol`, которое соответствует функции заглушки сочетаний клавиш для поиска.  
  
 `tagValue`  
 \[in\] значение тега указателя.  
  
 `rva`  
 \[in\] относительный виртуальный адрес.  
  
 `ppResult`  
 \[out\] указатель на указатель интерфейса `IDiaEnumSymbols`, который инициализируется с результатом.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод следует вызывать только в интерфейсе `IDiaSymbol`, который соответствует функции заглушки сочетаний клавиш.  
  
## См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)