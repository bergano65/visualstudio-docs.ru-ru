---
title: 'Ибиндевенсандлер:: Биндхандлер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 160020832509c9fb2aa95c095148127228a92e17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572568"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Привязывает событие к объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrEvent`  
 окне Указывает обрабатываемое событие.  
  
 `pdisp`  
 окне Указывает объект для обработчика события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод привязывает событие к объекту.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)