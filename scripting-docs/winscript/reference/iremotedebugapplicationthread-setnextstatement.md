---
title: IRemoteDebugApplicationThread::SetNextStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145178"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Принудительное выполнение продолжалось максимально близко к контексту данного кода в контексте заданного интервала.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 [in] Объект кадра стека. Этот аргумент может иметь значение NULL, что означает, что следует использовать текущий кадр стека.  
  
 `pCodeContext`  
 [in] Контекст кода. Этот аргумент может иметь значение NULL, что означает, что следует использовать текущий контекст кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывает принудительное выполнение продолжить максимально близко к контексту кода, определяемое `pCodeContext`, в контексте кадр, определяемый `pStackFrame`. Возможно, одно из этих аргументов `NULL`, представляющий текущий кадр или контекста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)