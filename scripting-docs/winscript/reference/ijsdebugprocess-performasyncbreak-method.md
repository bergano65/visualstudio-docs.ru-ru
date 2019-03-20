---
title: Метод IJsDebugProcess::PerformAsyncBreak | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a4fdb70341744c764779d406372bbd55418fd29
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150729"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>Метод IJsDebugProcess::PerformAsyncBreak
Помещает обработчик скриптов в режиме приостановки выполнения вызывает его на прерывание в следующей инструкции скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 [in] Идентификатор потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)