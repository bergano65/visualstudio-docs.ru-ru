---
title: Интерфейс IJsDebugStackWalker | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150898"
---
# <a name="ijsdebugstackwalker-interface"></a>Интерфейс IJsDebugStackWalker
Представляет средство просмотра стека для указанного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Получает следующий кадр.|  
  
## <a name="remarks"></a>Примечания  
 Средства обхода стека может создаваться только в тех случаях, пока целевой объект остановлен, а также являются недопустимыми после продолжается в целевом процессе.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)