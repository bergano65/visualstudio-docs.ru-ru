---
title: "IActiveScriptParse::InitNew | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Инициализирует обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка во время инициализации.  
  
## <a name="remarks"></a>Примечания  
 Перед тем как использовать обработчик скриптов, один из следующих методов необходимо вызвать: `IPersist*::Load`, `IPersist*::InitNew`, или `IActiveScriptParse::InitNew`. Этот метод Семантика идентична `IPersistStreamInit::InitNew`, в том, что этот метод указывает обработчик скриптов для инициализации самой себя. Обратите внимание, что оно является недопустимым для вызова оба `IPersist*::InitNew` или `IActiveScriptParse::InitNew` и `IPersist*::Load`, и не является допустимым для вызова `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, или `IPersist*::Load` более одного раза.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)