---
title: Метод IJsDebugDataTarget::AllocateVirtualMemory | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148468"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Метод IJsDebugDataTarget::AllocateVirtualMemory
Резервирует и(или) фиксирует область памяти в пространстве виртуальных адресов целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Адрес в целевом процессе, где память следует зафиксировать или зарезервировано. Это значение обычно равно нулю, в котором этом система выбирает адрес.  
  
 `size`  
 [in] Размер области памяти, в байтах. Система автоматически округлит до следующей границы страницы.  
  
 `allocationType`  
 [in] Указывает тип выделения для выполнения. Обычно это mem_commit &#124; MEM_RESERVE (0x3000) резервирует и фиксирует выделение в один шаг.  
  
 `pageProtection`  
 [in] Защита памяти для области страниц, которые должны быть выделены. Если страницы фиксируются, можно указать один из констант защиты памяти (например, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Базовый адрес выбранной области страниц.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Функция инициализирует память в ноль, если MEM_RESET не используется. Дополнительные сведения см. в API VirtualAlloc Win32.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)