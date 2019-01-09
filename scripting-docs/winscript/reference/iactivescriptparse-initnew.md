---
title: IActiveScriptParse::InitNew | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f0998bea50d7839f93111aa6b116934fae35bfa3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089990"
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