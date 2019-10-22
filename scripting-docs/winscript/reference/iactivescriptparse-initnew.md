---
title: 'IActiveScriptParse:: InitNew | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573514"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Инициализирует обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_FAIL`, если во время инициализации произошла ошибка.  
  
## <a name="remarks"></a>Заметки  
 Прежде чем можно будет использовать обработчик скриптов, необходимо вызвать один из следующих методов: `IPersist*::Load`, `IPersist*::InitNew` или `IActiveScriptParse::InitNew`. Семантика этого метода идентична `IPersistStreamInit::InitNew`, в том, что этот метод сообщает обработчику сценариев о необходимости инициализации. Обратите внимание, что не допускается вызов как `IPersist*::InitNew`, так `IActiveScriptParse::InitNew` и `IPersist*::Load`, а также не является допустимым для вызова `IPersist*::InitNew`, `IActiveScriptParse::InitNew` или `IPersist*::Load` более одного раза.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)