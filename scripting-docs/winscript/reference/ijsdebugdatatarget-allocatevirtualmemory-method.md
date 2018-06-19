---
title: Метод IJsDebugDataTarget::AllocateVirtualMemory | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728404"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Метод IJsDebugDataTarget::AllocateVirtualMemory
Резервирует или фиксирует области памяти в пределах виртуального адресного пространства целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [in] Адрес в пределах целевого процесса, где необходимо зафиксировать или зарезервированное памяти. Это значение обычно равно нулю, в котором случае система выбирает адреса.  
  
 `size`  
 [in] Размер области памяти для выделения в байтах. Система автоматически округлить до следующего границы страницы.  
  
 `allocationType`  
 [in] Указывает тип распределения для выполнения. Обычно это MEM_COMMIT &#124; MEM_RESERVE (0x3000), который резервирует и фиксирует выделение за один шаг.  
  
 `pageProtection`  
 [in] Защита памяти страниц, которые нужно выделить для области. Если фиксируются страницы можно указать один из констант защиты памяти (например, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Базовый адрес выделенной области страницы.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Функция инициализирует памяти, который выделяется память в нуль, если не используется MEM_RESET. Дополнительные сведения см. в разделе VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)