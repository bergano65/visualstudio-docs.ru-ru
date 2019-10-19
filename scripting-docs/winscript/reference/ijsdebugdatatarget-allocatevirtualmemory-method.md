---
title: 'Метод метод ijsdebugdatatarget:: Аллокатевиртуалмемори | Документация Майкрософт'
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577642"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Метод IJsDebugDataTarget::AllocateVirtualMemory
Резервирует или фиксирует область памяти в виртуальном адресном пространстве целевого процесса.  
  
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
 окне Адрес в целевом процессе, в котором память должна быть зафиксирована или зарезервирована. Это значение обычно равно нулю. в этом случае система выбирает адрес.  
  
 `size`  
 окне Размер выделяемой области памяти в байтах. Система автоматически округляет до границы следующей страницы.  
  
 `allocationType`  
 окне Указывает тип выполняемого выделения. Обычно это MEM_COMMIT &#124; MEM_RESERVE (0x3000), который резервирует и фиксирует выделение за один шаг.  
  
 `pageProtection`  
 окне Защита памяти для области выделяемых страниц. Если страницы зафиксированы, можно указать любую константу для защиты памяти (например, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 заполняет Базовый адрес выделенного региона страниц.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Функция инициализирует выделенную память до нуля, если не используется MEM_RESET. Дополнительные сведения см. в разделе API-интерфейс VirtualAlloc Win32.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)