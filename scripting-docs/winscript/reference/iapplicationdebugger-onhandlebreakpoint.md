---
title: 'Иаппликатиондебугжер:: Онхандлебреакпоинт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577832"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Обрабатывает событие точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prpt`  
 окне Поток, в котором произошла точка останова.  
  
 `br`  
 окне Причина точки останова.  
  
 `pError`  
 окне Сведения об ошибке времени выполнения, предоставляемые, если значение `br` BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывается при попадании в точку останова и вызове `IDebugApplication::HandleBreakPoint`.  
  
 Приложение будет оставаться приостановленным до тех пор, пока IDE отладчика не вызовет `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иаппликатиондебугжер](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication:: хандлебреакпоинт](../../winscript/reference/idebugapplication-handlebreakpoint.md)    
 [IRemoteDebugApplication:: ресумефромбреакпоинт](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)    
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)