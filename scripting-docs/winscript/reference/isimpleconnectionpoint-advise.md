---
title: ISimpleConnectionPoint::Advise | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c0ea37e6fabb051458a11c4838061126bd98bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091745"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Устанавливает соединение между объектом точки простого подключения и приемника клиента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdisp`  
 [in] Указатель на `IDispatch` приемнике уведомлений интерфейса на стороне клиента. Приемник клиента принимающий исходящие вызовы от точки простого подключения.  
  
 `pdwCookie`  
 [out] Указатель на возвращенный токен, который уникальным образом определяющий это соединение. Вызывающий объект использует этот токен позже для удаления соединения, передав его в `ISimpleConnectionPoint::Unadvise` метод. Если соединение не было успешно установлено, это значение равно нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод устанавливает соединение между объектом точки простого подключения и приемника клиента.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)