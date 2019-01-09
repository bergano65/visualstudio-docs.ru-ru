---
title: IApplicationDebugger::onDebugOutput | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebugOutput
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebugOutput
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed29673735038e9664324e9e342be199705348d5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088365"
---
# <a name="iapplicationdebuggerondebugoutput"></a>IApplicationDebugger::onDebugOutput
Обрабатывает событие выходные данные отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstr`  
 [in] Строка, отображаемая в отладчике.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Как правило, отладчик отображает `pstr` в окне вывода.  
  
 Этот метод вызывается, когда `IDebugApplication::DebugOutput` вызывается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)