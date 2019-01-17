---
title: IDebugApplication::FIsAutoJitDebugEnabled | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b06d223d76ed741eef6b379ace6b522248ded2e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348221"
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
 Если метод выполнен успешно и JIT-отладчик зарегистрирован в узлы ввода-вывода auto-debug, метод возвращает `TRUE`. В противном случае возвращает значение `FALSE`.  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, если JIT-отладчик был зарегистрирован для ввода-вывода узлы auto-debug.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)