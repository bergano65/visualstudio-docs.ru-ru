---
title: 'Метод метод ijsdebugdatatarget:: Фривиртуалмемори | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577622"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Метод IJsDebugDataTarget::FreeVirtualMemory
Выпуски или отменяют выделение области памяти в виртуальном адресном пространстве целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 окне Адрес в целевом процессе, в котором должна быть освобождена память.  
  
 `size`  
 окне Число байтов для отнесения. Чтобы освободить область памяти, это значение должно быть равно нулю.  
  
 `freeType`  
 окне Указывает тип выполняемой операции Free. Обычно это MEM_RELEASE (0x8000), который освобождает указанную область страниц. После операции страницы находятся в свободном состоянии. Вместо этого можно использовать MEM_DECOMMIT (0x4000), чтобы отменять фиксацию страниц без их освобождения.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Дополнительные сведения см. в разделе API-интерфейс функции VirtualFree для Win32.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)