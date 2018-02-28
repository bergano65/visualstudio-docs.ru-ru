---
title: "ISimpleConnectionPoint::Advise | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Устанавливает соединение между объектом точки простого подключения и приемником клиента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdisp`  
 [in] Указатель на `IDispatch` интерфейса на стороне клиента следует рекомендовать приемника. Приемник клиента получает исходящих вызовов от точки простого подключения.  
  
 `pdwCookie`  
 [out] Указатель на возвращаемый маркер, уникально определяющий это соединение. Вызывающий компонент использует этот токен позднее удалить подключение путем ее передачи `ISimpleConnectionPoint::Unadvise` метод. Если соединение не было успешно установлено, это значение равно нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод устанавливает соединение между объектом точки простого подключения и приемником клиента.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)