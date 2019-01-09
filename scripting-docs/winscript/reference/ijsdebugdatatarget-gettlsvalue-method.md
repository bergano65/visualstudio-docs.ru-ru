---
title: Метод IJsDebugDataTarget::GetTlsValue | Документация Майкрософт
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
ms.openlocfilehash: 8f81e9ea6cca9bf54753a496e07903d23bb913fc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095333"
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