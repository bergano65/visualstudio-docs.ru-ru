---
title: 'Метод метод ijsdebugprocess:: Креатестакквалкер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573828"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>Метод IJsDebugProcess::CreateStackWalker
Фабричный метод для обхода стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 окне Идентификатор потока.  
  
 `ppStackWalker`  
 заполняет Новый объект обходчика стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает E_JsDEBUG_UNKNOWN_THREAD, если в потоке отсутствует JavaScript. Этот метод может быть вызван только в том случае, если целевой процесс остановлен.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)