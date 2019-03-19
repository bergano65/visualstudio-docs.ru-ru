---
title: Метод IJsDebugFrame::GetStackRange | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 52dd6114d3ec462f91f8bce5e76f73c5487746ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147440"
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