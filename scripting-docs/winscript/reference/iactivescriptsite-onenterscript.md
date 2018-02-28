---
title: "IActiveScriptSite::OnEnterScript | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Уведомляет узел, обработчик сценариев начал выполнение кода скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов необходимо вызвать этот метод для каждой записи или повторный вход в обработчик сценариев. Например, если скрипт вызывает объект, который затем инициирует событие обработано обработчиком сценариев, обработчик сценариев необходимо вызвать `IActiveScriptSite::OnEnterScript` до выполнения события и необходимо вызвать [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) метод после выполнения события, но перед возвратом, инициировавший событие. Вызов этого метода могут быть вложенными. Каждый вызов этого метода требуется соответствующий вызов `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)