---
title: Метод IJsDebugFrame::GetDebugProperty | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b8640eb2bad9633e77797a5ce2348833dbee80d6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089912"
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