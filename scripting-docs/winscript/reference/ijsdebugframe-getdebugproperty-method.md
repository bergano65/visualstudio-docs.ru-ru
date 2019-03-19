---
title: Метод IJsDebugFrame::GetDebugProperty | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDebugProperty
apilocation:
- jscript9diag.dll
ms.assetid: 19bfbe9e-323e-4fe7-ac0e-dc9e87d53219
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3ababdae51e95d6a3234c4e55f3e20ffa5fd760
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147414"
---
# <a name="ijsdebugframegetdebugproperty-method"></a>Метод IJsDebugFrame::GetDebugProperty
Возвращает браузер свойств для этого кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDebugProperty(  
   IJsDebugProperty **ppDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDebugProperty`  
 [out] Объект, представляющий обозреватель свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)