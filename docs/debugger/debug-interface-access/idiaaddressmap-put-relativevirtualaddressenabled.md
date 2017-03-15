---
title: "IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_relativeVirtualAddressEnabled - метод"
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Позволяет клиенту включить или отключить вычисление и использование относительных виртуальных адресов \(RVA\).  
  
## Синтаксис  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### Параметры  
 NewVal  
 \[in\] имеет значение `TRUE` включение или  `FALSE` отключить.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Адреса для отладки объектов, описанные в интерфейсах DIA и по отношению к основанию образа исполняемого файла, могут быть получены как относительные виртуальные адреса.  
  
 Использование Rva включена, когда сегменты исходного загружаются из файла PDB.  Чтобы получить текущее состояние использования Rva, вызовите [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) метод.  
  
 `put_relativeVirtualAddress` метод необходимо вызывать, чтобы включить Rva после успешного вызова  [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод устанавливал новые заголовки образа.  
  
## См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)