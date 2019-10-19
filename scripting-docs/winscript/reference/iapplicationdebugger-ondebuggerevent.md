---
title: 'Иаппликатиондебугжер:: Ондебугжеревент | Документация Майкрософт'
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
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577865"
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
 окне Идентификатор интерфейса для объекта.  
  
 `punk`  
 окне Объект события, реализующий интерфейс, определенный `riid`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод в настоящее время не реализован.|  
  
## <a name="remarks"></a>Заметки  
 Семантика `IUnknown` полностью определена как Application/Debugger.  
  
 Этот метод позволяет применять пользовательские расширения модели отладчика. в настоящее время он не реализован.  
  
 Этот метод вызывается при вызове `IDebugApplication::FireDebuggerEvent`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иаппликатиондебугжер](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)