---
title: 'Иенумдебугпропертинфо:: Skip | Документация Майкрософт'
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
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574155"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Пропускает указанное число структур `DebugPropertyInfo` в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 окне Число пропускаемых структур `DebugPropertyInfo` в последовательности перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`. Возвращает `S_FALSE` и задает указатель текущего элемента на конец перечисления, если `celt` больше числа элементов, оставшихся в перечислителе.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иенумдебугпропертинфо](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)