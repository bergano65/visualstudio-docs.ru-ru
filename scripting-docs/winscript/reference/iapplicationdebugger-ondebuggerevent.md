---
title: IApplicationDebugger::onDebuggerEvent | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78bb3345463dfd682534dc60a216f3e0e8fdf2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991364"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Обрабатывает событие пользовательского приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `riid`  
 [in] Идентификатор для объекта.  
  
 `punk`  
 [in] Объект события, который реализует интерфейс, определяемый `riid`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод еще не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Семантика `IUnknown` является полностью определенные приложения и отладчика.  
  
 Этот метод позволяет для пользовательских расширений модели отладчика; он еще не реализован.  
  
 Этот метод вызывается, когда `IDebugApplication::FireDebuggerEvent` вызывается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)