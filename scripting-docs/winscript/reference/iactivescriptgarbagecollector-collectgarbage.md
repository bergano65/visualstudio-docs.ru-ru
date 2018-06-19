---
title: IActiveScriptGarbageCollector::CollectGarbage | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645734"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Активных скриптов основное приложение вызывает этот метод для запуска сборки мусора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptgctype`  
 [in] [Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) , указывает, следует ли выполнить сборку мусора обычный или полным.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)