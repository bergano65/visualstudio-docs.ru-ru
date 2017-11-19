---
title: "IDebugApplication::FireDebuggerEvent | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cb02390602b6b93b8c233f245ede395833d67e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Универсальный событие в отладчик `IApplicationDebugger` интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `riid`  
 [in] Идентификатор GUID для объекта.  
  
 `punk`  
 [in] Объект события для передачи в отладчик.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован в настоящее время.|  
  
## <a name="remarks"></a>Примечания  
 Семантика GUID и `IUnknown` являются полностью определенные приложения и отладчика.  
  
 Этот метод позволяет для пользовательских расширений модели отладчика. он еще не реализован.  
  
 Этот метод вызывает `IApplicationDebugger::onDebuggerEvent` для вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)