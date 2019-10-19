---
title: 'Метод метод ijsdebugframe:: GetStackRange | Документация Майкрософт'
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
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574038"
---
# <a name="ijsdebugframegetstackrange-method"></a>Метод IJsDebugFrame::GetStackRange
Возвращает диапазон абсолютных адресов логического кадра стека JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStart`  
 заполняет Самый нижний указатель стека фрейма.  
  
 `pEnd`  
 заполняет Самый верхний указатель укладчика рамки.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Этот метод полезен для пиеЦинг вместе чередующихся трассировок стека, собранных из нескольких сред выполнения. Начальные и конечные указатели стека могут охватывать несколько кадров стека физического компьютера (для интерпретируемых фреймов среды выполнения JavaScript). Начало >, так как стек растет с самого высокого до младшего адреса.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)