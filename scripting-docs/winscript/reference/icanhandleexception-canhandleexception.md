---
title: 'Иканхандликсцептион:: Канхандликсцептион | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575723"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Определяет, может ли вызывающий объект обработчика скриптов управлять указанным исключением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExcepInfo`  
 окне Указатель на структуру `EXCEPINFO`, содержащую сведения, которые будут переданы, если обработчик исключений не найден.  
  
 `pvar`  
 окне Значение, связанное с исключением, например значение, выдаваемое инструкцией `throw`. Этот параметр может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Вызывающий объект может справиться с исключением|  
|`E_FAIL`|Вызывающий объект не может справиться с исключением.|  
  
## <a name="remarks"></a>Заметки  
 Если вызов `IDispatchEx::InvokeEx` или аналогичный метод приводит к исключению, обработчик скриптов проверяет наличие вызывающего объекта в цепочке вызывающих объектов сценария, которая поддерживает интерфейс `ICanHandleException` и указывает, что он может справиться с исключением. Если ни один из вызывающих объектов не может справиться с исключением, обработчик скриптов останавливается.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иканхандликсцептион](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)