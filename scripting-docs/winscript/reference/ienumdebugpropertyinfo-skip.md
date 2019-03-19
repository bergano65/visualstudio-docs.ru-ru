---
title: IEnumDebugPropertyInfo::Skip | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7544b8ea54fabc53e6c8476648e339c53da94d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150742"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Пропускает заданное число `DebugPropertyInfo` структур в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество `DebugPropertyInfo` структур в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`. Возвращает `S_FALSE` и устанавливает указатель текущего элемента и заканчивая перечисления, если `celt` больше, чем число элементов слева в перечислителе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)