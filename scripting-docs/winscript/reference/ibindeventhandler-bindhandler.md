---
title: IBindEventHandler::BindHandler | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 62ac6de8342f0a436d984f4194351507fdcd5edd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090718"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Связывает событие объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrEvent`  
 [in] Указывает события для обработки.  
  
 `pdisp`  
 [in] Указывает объект для обработки события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод привязывает событие для объекта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)