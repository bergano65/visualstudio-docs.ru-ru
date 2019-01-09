---
title: Метод IJsDebugFrame::GetStackRange | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090289"
---
# <a name="ijsdebugframegetstackrange-method"></a>Метод IJsDebugFrame::GetStackRange
Возвращает диапазон абсолютных адресов логического фрейма стеков JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStart`  
 [out] Bottom большинство указателя стека кадра.  
  
 `pEnd`  
 [out] Первые самый верхний указатель на кадр.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Этот метод полезен для соединения вместе перемежаемых трассировок стека с множественными средами выполнения. Начало, конечные указатели стека может охватывать несколько кадров стека физического компьютера (для интерпретированных кадров среды выполнения JavaScript). Пуск > завершить, так как стек растет от большего к минимальным адресам.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)