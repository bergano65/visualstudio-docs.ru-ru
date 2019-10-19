---
title: 'Метод метод ijsdebugdatatarget:: GetThreadContext | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577656"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>Метод IJsDebugDataTarget::GetThreadContext
Извлекает контекст для данного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 окне Поток, выполняющийся в целевом процессе.  
  
 `contextFlags`  
 окне Задает флаги контекста. Это то же самое, что и поле Контекстфлагс CONTEXT (Дополнительные сведения см. в разделе Winnt. h, найдите CONTEXT_ALL).  
  
 `contextSize`  
 окне Размер буфера, заданного параметром Пконтекст.  
  
 `pContext`  
 заполняет Получает структуру контекста, зависящую от платформы, в буфер, указанный параметром Пконтекст.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)