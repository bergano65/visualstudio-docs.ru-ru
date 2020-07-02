---
title: 'IActiveScriptParse32:: InitNew | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835710"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Инициализирует обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` , если операция завершилась успешно, или при возникновении `E_FAIL` ошибки во время инициализации.  
  
## <a name="remarks"></a>Комментарии  
 Прежде чем можно будет использовать обработчик скриптов, необходимо вызвать один из следующих методов: `IPersist*::Load` , `IPersist*::InitNew` или `IActiveScriptParse32::InitNew` . Семантика этого метода идентична `IPersistStreamInit::InitNew` , в том, что этот метод указывает обработчику сценариев инициализировать сам себя. Обратите внимание, что недопустимо вызывать и `IPersist*::InitNew` , `IActiveScriptParse32::InitNew` и `IPersist*::Load` , и не может вызывать `IPersist*::InitNew` , `IActiveScriptParse32::InitNew` или `IPersist*::Load` несколько раз.  
  
## <a name="see-also"></a>Дополнительно  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)