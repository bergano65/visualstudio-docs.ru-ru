---
title: Интерфейс Ижсдебугстакквалкер | Документация Майкрософт
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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574017"
---
# <a name="ijsdebugstackwalker-interface"></a>Интерфейс IJsDebugStackWalker
Представляет обход стека для указанного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Метод IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Возвращает следующий кадр.|  
  
## <a name="remarks"></a>Заметки  
 Пошаговые руководства стека могут быть созданы только в том случае, если целевой объект остановлен, и являются недопустимыми после того, как целевой процесс будет снова продолжен.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)