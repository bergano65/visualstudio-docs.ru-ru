---
title: Метод IJsDebugDataTarget::ReadMemory | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66d3709dadfc8da2feb7e6845a7aeaa357235d9e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089184"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Метод IJsDebugDataTarget::ReadMemory
Читает содержимое памяти целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [in] Базовый адрес, из которого считывается в память целевого процесса.  
  
 `flags`  
 [in] Флаги, контролирующие поведение ReadMemory.  
  
 `pBuffer`  
 [out] Буфер, получающий содержимое из адресного пространства целевого процесса. В случае сбоя содержимое данного буфера не определено.  
  
 `size`  
 [in] Число байтов, считываемых из процесса.  
  
 `pBytesRead`  
 [out] Указывает число байтов, считанных из целевого процесса. Если JsDebugAllowPartialRead снят, при успешном завершении это значение всегда будет точно равно размеру ввода. Если JsDebugAllowPartialRead задан, в случае успеха, это значение будет больше нуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает значение s_ок в успехе и коды ошибок используются для любой ошибки. Возвращает E_JsDEBUG_INVALID_MEMORY_ADDRESS, если адрес является недопустимым. Дополнительные сведения см. в разделе JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)