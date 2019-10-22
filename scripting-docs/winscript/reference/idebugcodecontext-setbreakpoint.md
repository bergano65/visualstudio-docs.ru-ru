---
title: 'Идебугкодеконтекст:: Сетбреакпоинт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2bb0395cc1aeaceda3763b2c4016bbd9ba7e1f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573209"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Задает или очищает точку останова в данном контексте кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bps`  
 окне Задает состояние точки останова для этого контекста кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод задает или очищает точку останова в данном контексте кода.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугкодеконтекст](../../winscript/reference/idebugcodecontext-interface.md)  
 [Перечисление BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)