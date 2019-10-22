---
title: Метод ijsdebugprocess::P метод Ерформасинкбреак | Документация Майкрософт
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
ms.openlocfilehash: 3320c59097dec5229030a3f15252d907562c67e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577336"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>Метод IJsDebugProcess::PerformAsyncBreak
Помещает обработчик сценария в режим приостановки, в результате чего он останавливается на следующей инструкции сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 окне Идентификатор потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)