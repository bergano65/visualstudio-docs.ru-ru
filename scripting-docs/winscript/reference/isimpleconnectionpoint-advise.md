---
title: 'Исимплеконнектионпоинт:: Advise | Документация Майкрософт'
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
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571836"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Устанавливает соединение между простым объектом точки подключения и приемником клиента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdisp`  
 окне Указатель на интерфейс `IDispatch` в приемнике уведомлений клиента. Приемник клиента получает исходящие вызовы от простой точки подключения.  
  
 `pdwCookie`  
 заполняет Указатель на возвращаемый токен, однозначно определяющий это соединение. Вызывающий объект использует этот токен позже, чтобы удалить соединение, передав его методу `ISimpleConnectionPoint::Unadvise`. Если подключение не было установлено успешно, это значение равно нулю.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод устанавливает соединение между простым объектом точки подключения и приемником клиента.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса исимплеконнектионпоинт](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)