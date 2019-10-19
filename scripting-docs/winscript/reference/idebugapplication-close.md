---
title: 'IDebugApplication:: Close | Документация Майкрософт'
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
ms.openlocfilehash: 0445e9aed990da684efac6675e05183fd939973f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575581"
---
# <a name="idebugapplicationclose"></a>IDebugApplication::Close
Заставляет приложение освобождать все ссылки и переходить в неактивное состояние.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Как правило, владелец приложения вызывает этот метод при выходе из приложения.  
  
 Этот метод вызывает `IApplicationDebugger::onClose`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)