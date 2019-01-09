---
title: ISimpleConnectionPoint::Unadvise | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83fdf8f6a6e9378d328a9df61b1561a1ae747ae8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089275"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Завершает вспомогательное соединение, установленное ранее при помощи `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCookie`  
 [in] Маркер подключения для прерывания, возвращенный `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 При завершении вспомогательное соединение, подключение точки вызовы `Release` метод на указатель, который был сохранен для подключения во время `ISimpleConnectionPoint::Advise` метод. Которые вызывают Обращает `AddRef` , было выполнено в течение `ISimpleConnectionPoint::Advise` когда точка подключения вызывает приемнике уведомлений `QueryInterface`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)