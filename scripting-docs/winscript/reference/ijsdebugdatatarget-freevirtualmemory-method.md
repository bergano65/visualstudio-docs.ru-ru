---
title: Метод IJsDebugDataTarget::FreeVirtualMemory | Документация Майкрософт
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
ms.openlocfilehash: ed5fabfca8ac9b0e9fe0dfba346b0354f4c0576f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086805"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Метод IJsDebugDataTarget::FreeVirtualMemory
Выпускает и(или) отменяет фиксацию области памяти в пространстве виртуальных адресов целевого процесса.  
  
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
 [in] Адрес в целевом процессе, где память должна освобождаться.  
  
 `size`  
 [in] Число байтов для отмены фиксации. Чтобы освободить область памяти, это значение должно равняться нулю.  
  
 `freeType`  
 [in] Указывает тип свободной операции для выполнения. Обычно это MEM_RELEASE (0x8000), который выпускает заданную область страниц. После выполнения операции страницы будут находиться в свободном состоянии. MEM_DECOMMIT (0x4000) можно использовать для отмены фиксации страниц без последующего их отпускания.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в API VirtualFree Win32.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)