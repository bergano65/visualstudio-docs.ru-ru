---
title: 'Иремотедебугаппликатионсреад:: Сетнекстстатемент | Документация Майкрософт'
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
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575506"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Заставляет выполнение выполняться как можно ближе к заданному контексту кода в контексте данного кадра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 окне Объект кадра стека. Этот аргумент может иметь значение NULL, что означает, что следует использовать текущий кадр стека.  
  
 `pCodeContext`  
 окне Контекст кода. Этот аргумент может иметь значение NULL, что означает, что следует использовать текущий контекст кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод заставляет выполнение выполняться как можно ближе к контексту кода, заданному `pCodeContext`, в контексте кадра, заданном `pStackFrame`. Любой из этих аргументов может быть `NULL`, представляющей текущий кадр или контекст.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)