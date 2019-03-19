---
title: IActiveScriptGarbageCollector::CollectGarbage | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144671"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Узла активного скрипта вызывает этот метод, чтобы запустить сбор мусора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptgctype`  
 [in] [Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) , указывающее, следует ли выполнить сборку мусора обычное или полное.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)