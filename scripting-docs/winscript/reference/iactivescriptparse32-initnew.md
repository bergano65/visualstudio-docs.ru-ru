---
title: "IActiveScriptParse32::InitNew | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Инициализирует обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка во время инициализации.  
  
## <a name="remarks"></a>Примечания  
 Перед тем как использовать обработчик скриптов, один из следующих методов необходимо вызвать: `IPersist*::Load`, `IPersist*::InitNew`, или `IActiveScriptParse32::InitNew`. Этот метод Семантика идентична `IPersistStreamInit::InitNew`, в том, что этот метод указывает обработчик скриптов для инициализации самой себя. Обратите внимание, что оно является недопустимым для вызова оба `IPersist*::InitNew` или `IActiveScriptParse32::InitNew` и `IPersist*::Load`, и не является допустимым для вызова `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, или `IPersist*::Load` более одного раза.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)