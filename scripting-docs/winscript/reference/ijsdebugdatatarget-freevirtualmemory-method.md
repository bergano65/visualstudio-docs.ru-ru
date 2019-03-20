---
title: Метод IJsDebugDataTarget::FreeVirtualMemory | Документация Майкрософт
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
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146309"
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