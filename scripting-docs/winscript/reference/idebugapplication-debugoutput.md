---
title: "IDebugApplication::DebugOutput | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc956c7d2d65d20788a79c9f685e386aba97a80
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
В результате заданной строки, которые должны отображаться в отладчике интегрированной среды разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT DebugOutput(  
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
 Этот метод позволяет языковая подсистема реализовать поддержку отладки выходных данных для конкретного языка. Строка, как правило, отображается в окне вывода.  
  
 Этот метод вызывает `IApplicationDebugger::onDebugOutput` для вызова.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)