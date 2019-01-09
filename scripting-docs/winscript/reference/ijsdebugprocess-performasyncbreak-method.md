---
title: Метод IJsDebugProcess::PerformAsyncBreak | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a614bbfdde117ba223ca3f8f3d8b9b77c44c4393
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089145"
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