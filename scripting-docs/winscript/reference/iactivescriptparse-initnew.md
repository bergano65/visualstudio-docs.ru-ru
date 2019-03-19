---
title: IActiveScriptParse::InitNew | Документация Майкрософт
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
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148952"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Инициализирует обработчика скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка во время инициализации.  
  
## <a name="remarks"></a>Примечания  
 Прежде чем можно будет использовать обработчик скриптов, один из следующих методов необходимо вызвать: `IPersist*::Load`, `IPersist*::InitNew`, или `IActiveScriptParse::InitNew`. Этот метод Семантика идентична `IPersistStreamInit::InitNew`, в том, что этот метод указывает на обработчик скриптов инициализировать самого себя. Обратите внимание, что не допускается вызывать оба `IPersist*::InitNew` или `IActiveScriptParse::InitNew` и `IPersist*::Load`, не является допустимым для вызова `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, или `IPersist*::Load` более одного раза.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)