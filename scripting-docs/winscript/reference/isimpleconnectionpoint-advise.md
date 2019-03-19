---
title: ISimpleConnectionPoint::Advise | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153114"
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