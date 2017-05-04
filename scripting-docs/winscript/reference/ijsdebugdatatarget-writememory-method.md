---
title: "Метод IJsDebugDataTarget::WriteMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::WriteMemory
Читает содержимое памяти целевого процесса.  
  
## Синтаксис  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Базовый адрес, по которому следует записывать память целевого процесса.  
  
 `pMemory`  
 \[in\] Данные для записи в адресном пространстве указанного процесса.  
  
 `size`  
 \[in\] Число байтов для записи в текущий процесс.  
  
## Возвращаемое значение  
  
## Заметки  
 Прежде чем происходит передача данных, система проверяет, что все данные в базовом адресе и память указанного размера доступны для записи и, если они не доступны, функция вызывает ошибку E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)