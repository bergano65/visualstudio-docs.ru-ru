---
title: "Метод IJsDebugDataTarget::ReadMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::ReadMemory
Читает содержимое памяти целевого процесса.  
  
## Синтаксис  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Базовый адрес, по которому следует читать память целевого процесса.  
  
 `flags`  
 \[in\] Флаги, контролирующие поведение ReadMemory.  
  
 `pBuffer`  
 \[out\] Буфер, который получает содержимое из адресного пространства целевого процесса.  При сбое содержимое этого буфера не задается.  
  
 `size`  
 \[in\] Максимальное число байтов, которое должно быть считано из текущего процесса.  
  
 `pBytesRead`  
 \[out\] Показывает количество байтов, считываемых из целевого процесса.  Если флаг JsDebugAllowPartialRead снят, при успешном завершении это значение всегда будет точно равно размеру ввода.  Если JsDebugAllowPartialRead задан, при успешном завершении это значение будет больше нуля.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает значение S\_ОК в успехе и коды ошибок используются для любой ошибки.  Возвращает E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS, если адрес недопустим.  Дополнительные сведения см. в описании JsDebugAllowPartialRead.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)