---
title: IDebugApplication::FIsAutoJitDebugEnabled | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f594c5ce48ebd31a265ed438db176c5707d9b079
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990866"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Определяет, зарегистрирован ли just-in-time (JIT) отладчик к узлам ввода-вывода auto-debug.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод выполнен успешно и JIT-отладчик зарегистрирован в узлы ввода-вывода auto-debug, метод возвращает `TRUE`. В противном случае она возвращает `FALSE`.  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, если JIT-отладчик был зарегистрирован для ввода-вывода узлы auto-debug.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)