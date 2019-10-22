---
title: 'IDebugApplication:: Фиредебугжеревент | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575000"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Вызывает универсальное событие в интерфейсе `IApplicationDebugger` отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `riid`  
 окне Идентификатор GUID для объекта.  
  
 `punk`  
 окне Объект события, передаваемый отладчику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод в настоящее время не реализован.|  
  
## <a name="remarks"></a>Заметки  
 Семантика GUID и `IUnknown` полностью определена как Application/Debugger.  
  
 Этот метод позволяет применять пользовательские расширения модели отладчика. в настоящее время он не реализован.  
  
 Этот метод вызывает `IApplicationDebugger::onDebuggerEvent`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)