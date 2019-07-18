---
title: Метод IJsDebugDataTarget::GetTlsValue | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582814"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Метод IJsDebugDataTarget::GetTlsValue
Для отлаживаемого потока извлекает значение в области потока локальное хранилище (TLS) для указанного индекса TLS.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 [in] Поток, выполняемый в целевом процессе для чтения из.  
  
 `tlsIndex`  
 [in] Индекс TLS, который был выделен, когда целевой процесс вызвал функцию TlsAlloc.  
  
 `pValue`  
 [out] Значение размера указателя, которое было сохранено в слоте TLS потока. Если целевой поток 32-разрядный, верхние 32 бита этого значения будут равны нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Каждый поток процесса имеет собственную ячейку для каждого индекса TLS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)