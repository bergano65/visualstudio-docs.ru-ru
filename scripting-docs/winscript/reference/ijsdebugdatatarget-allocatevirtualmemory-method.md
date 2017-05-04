---
title: "Метод IJsDebugDataTarget::AllocateVirtualMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::AllocateVirtualMemory
Резервирует и\(или\) фиксирует область памяти в пространстве виртуальных адресов целевого процесса.  
  
## Синтаксис  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Адрес в целевом процессе, где необходимо зафиксировать или зарезервировать память.  Это значение обычно равно нулю, при этом система выбирает адрес.  
  
 `size`  
 \[in\] Размер выделяемой области памяти \(в байтах\).  Система автоматически округлит до следующей границы страницы.  
  
 `allocationType`  
 \[in\] указывает тип выделения для выполнения.  Обычно это MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\) резервирует и фиксирует выделение в один шаг.  
  
 `pageProtection`  
 \[in\] Защита памяти для выделяемой области страниц.  Если страницы фиксируются, можно указать любую из констант защиты памяти \(например, PAGE\_READWRITE, PAGE\_EXECUTE\).  
  
 `pAllocatedAddress`  
 \[out\] Базовый адрес выбранной области страниц.  
  
## Возвращаемое значение  
  
## Заметки  
 Функция инициализирует память, выделенную в ноль, если MEM\_RESET не используется.  Дополнительные сведения см. в API VirtualAlloc Win32.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)