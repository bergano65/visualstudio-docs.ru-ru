---
title: IDebugApplication::FCanJitDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6808c8bb7e27e7b416e79b2f23e323c3ae3a528f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095359"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Определяет, зарегистрирован ли отладчик just-in-time (JIT).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается успешно, и регистрируется JIT-отладчик, метод возвращает `TRUE`. В противном случае возвращает значение `FALSE`.  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, зарегистрирован ли JIT-отладчик.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)