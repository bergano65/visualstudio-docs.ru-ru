---
title: 'IActiveScriptParse32:: InitNew | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561657"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32:: InitNew
Инициализирует обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_FAIL`, если во время инициализации произошла ошибка.  
  
## <a name="remarks"></a>Заметки  
 Прежде чем можно будет использовать обработчик скриптов, необходимо вызвать один из следующих методов: `IPersist*::Load`, `IPersist*::InitNew` или `IActiveScriptParse32::InitNew`. Семантика этого метода идентична `IPersistStreamInit::InitNew`, в том, что этот метод сообщает обработчику сценариев о необходимости инициализации. Обратите внимание, что не допускается вызов как `IPersist*::InitNew`, так `IActiveScriptParse32::InitNew` и `IPersist*::Load`, а также не является допустимым для вызова `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` или `IPersist*::Load` более одного раза.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)