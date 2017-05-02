---
title: "Метод IJsDebugDataTarget::FreeVirtualMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::FreeVirtualMemory
Выпускает и\(или\) отменяет фиксацию области памяти в пространстве виртуальных адресов целевого процесса.  
  
## Синтаксис  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Адрес в целевом процессе, память в котором необходимо освободить.  
  
 `size`  
 \[входящий\] Число байтов для отмены фиксации.  Чтобы освободить область памяти, это значение должно быть равно нулю.  
  
 `freeType`  
 \[in\] указывает тип свободной операции для выполнения.  Обычно это MEM\_RELEASE \(0x8000\), который выпускает заданную область страниц.  После этой операции страницы будут находиться в свободном состоянии.  MEM\_DECOMMIT \(0x4000\) можно использовать вместо того, чтобы отменять фиксацию страниц без освобождения.  
  
## Возвращаемое значение  
  
## Заметки  
 Дополнительные сведения см. в API VirtualFree Win32.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)