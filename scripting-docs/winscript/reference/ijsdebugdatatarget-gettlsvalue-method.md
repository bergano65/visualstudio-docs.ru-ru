---
title: Метод IJsDebugDataTarget::GetTlsValue | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727884"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Метод IJsDebugDataTarget::GetTlsValue
Получает значение в области потока локальное хранилище (TLS) с указанным индексом TLS отлаживаемый поток.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 [in] Поток, выполняющийся в целевом процессе, из которого выполняется чтение.  
  
 `tlsIndex`  
 [in] Индекс TLS, который был выделен вызова функции TlsAlloc целевого процесса.  
  
 `pValue`  
 [out] Значение размером указателя, которое было сохранено в слоте TLS потока. Если целевой поток является 32-разрядным, верхние 32-бит это значение будет равно нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Каждый поток процесса имеет свой собственный слот для каждого индекса TLS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)