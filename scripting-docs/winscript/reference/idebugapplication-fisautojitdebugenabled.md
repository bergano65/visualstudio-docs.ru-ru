---
title: 'IDebugApplication:: Фисаутожитдебуженаблед | Документация Майкрософт'
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
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574992"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Определяет, зарегистрирован ли JIT-отладчик для автоматической отладки узлов глупы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается, и JIT-отладчик зарегистрирован для автоматической отладки узлов глупы, метод возвращает `TRUE`. В противном случае возвращает значение `FALSE`.  
  
## <a name="remarks"></a>Заметки  
 Этот метод определяет, зарегистрирован ли JIT-отладчик для автоматической отладки узлов глупы.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)