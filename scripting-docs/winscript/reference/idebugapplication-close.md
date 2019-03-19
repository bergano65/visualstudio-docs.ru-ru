---
title: IDebugApplication::Close | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::Close
ms.assetid: d19baa07-3f3b-47de-8185-5eb3e7ac8b46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d93262e5875d5b51f7cf306409609671e8157cc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153452"
---
# <a name="idebugapplicationclose"></a>IDebugApplication::Close
Вызывает это приложение освободить все ссылки и введите в неактивном состоянии.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Как правило, владелец приложения этот метод вызывается при выходе приложения.  
  
 Этот метод вызывает `IApplicationDebugger::onClose` для вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)