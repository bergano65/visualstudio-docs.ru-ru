---
title: Метод IJsDebugDataTarget::FreeVirtualMemory | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728744"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Метод IJsDebugDataTarget::FreeVirtualMemory
Освобождает или снимает выделение области памяти в пределах виртуального адресного пространства целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [in] Адрес в целевом процессе, где следует освободить память.  
  
 `size`  
 [in] Число байтов для фиксации. Чтобы освободить это область памяти, это значение должно равняться нулю.  
  
 `freeType`  
 [in] Указывает тип выполняемой операции бесплатно. Обычно это MEM_RELEASE (0x8000), который высвобождает заданной области страницы. После выполнения операции страницы находятся в свободном состоянии. MEM_DECOMMIT (0x4000) можно использовать для фиксации страниц без их освобождения.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в разделе VirtualFree Win32 API.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)