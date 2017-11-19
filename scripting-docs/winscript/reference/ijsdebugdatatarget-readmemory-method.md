---
title: "Метод IJsDebugDataTarget::ReadMemory | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Метод IJsDebugDataTarget::ReadMemory
Считывает память целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Базовый адрес, из которого выполняется чтение памяти в целевом процессе.  
  
 `flags`  
 [in] Флаги управления поведением ReadMemory.  
  
 `pBuffer`  
 [out] Буфер, получающий содержимое из адресное пространство целевого процесса. В случае сбоя содержимое данного буфера не определено.  
  
 `size`  
 [in] Число байтов, считываемых из процесса.  
  
 `pBytesRead`  
 [out] Указывает число байтов, считанных из целевого процесса. Если снять JsDebugAllowPartialRead, в случае успешного выполнения это значение всегда будет точно равно размер входных данных. Если указан JsDebugAllowPartialRead, в случае успеха, это значение будет больше нуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает значение S_OK, в случае успеха и коды ошибок используются для любой ошибки. Возвращает E_JsDEBUG_INVALID_MEMORY_ADDRESS, если адрес является недопустимым. Дополнительные сведения см. в разделе JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)