---
title: 'Метод метод ijsdebugdatatarget:: ReadMemory | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572434"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Метод IJsDebugDataTarget::ReadMemory
Считывает память целевого процесса.  
  
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
 окне Базовый адрес, из которого считывается память целевого процесса.  
  
 `flags`  
 окне Флаги, управляющие поведением ReadMemory.  
  
 `pBuffer`  
 заполняет Буфер, который получает содержимое из адресного пространства целевого процесса. В случае сбоя содержимое этого буфера не указано.  
  
 `size`  
 окне Число байтов, считываемых из процесса.  
  
 `pBytesRead`  
 заполняет Указывает число байтов, считанных из целевого процесса. Если Жсдебугалловпартиалреад является очевидным, при успешном выполнении это значение всегда будет точно равно размеру входных данных. Если указан параметр Жсдебугалловпартиалреад, значение в случае успешного выполнения будет больше нуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает значение S_OK при успешном выполнении, и коды ошибок используются для любой ошибки. Возвращает E_JsDEBUG_INVALID_MEMORY_ADDRESS, если адрес является недопустимым. Дополнительные сведения см. в разделе Жсдебугалловпартиалреад.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)