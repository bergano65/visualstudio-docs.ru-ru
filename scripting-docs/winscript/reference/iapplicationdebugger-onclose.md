---
title: 'Иаппликатиондебугжер:: OnClose | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577873"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Обрабатывает событие закрытия приложения отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывается при вызове `IDebugApplication::Close`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иаппликатиондебугжер](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)