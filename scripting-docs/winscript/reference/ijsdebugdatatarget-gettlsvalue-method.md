---
title: 'Метод метод ijsdebugdatatarget:: GetTlsValue | Документация Майкрософт'
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
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577609"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Метод IJsDebugDataTarget::GetTlsValue
Для отлаживаемого потока получает значение в слоте локального хранилища потока (TLS) для указанного индекса TLS.  
  
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
 окне Поток, выполняющийся в целевом процессе чтения из.  
  
 `tlsIndex`  
 окне Индекс TLS, который был выделен, когда целевой процесс вызвал функцию TlsAlloc.  
  
 `pValue`  
 заполняет Значение размера указателя, которое было сохранено в слоте TLS потока. Если целевой поток является 32-битным, верхние 32-разряды этого значения будут равны нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Каждый поток процесса имеет собственный слот для каждого индекса TLS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)