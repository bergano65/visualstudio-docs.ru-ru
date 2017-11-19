---
title: "IActiveScriptSite::OnLeaveScript | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Уведомляет основное приложение о возврате обработчик скриптов выполнять код скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов необходимо вызвать этот метод перед возвратом управления вызывающему приложению, введенного обработчика скриптов. Например, если скрипт вызывает объект, который затем инициирует событие обработано обработчиком сценариев, обработчик сценариев необходимо вызвать [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) метод перед выполнением события и необходимо вызвать `IActiveScriptSite::OnLeaveScript`после выполнения события перед возвратом, инициировавший событие. Вызов этого метода могут быть вложенными. Каждый вызов `IActiveScriptSite::OnEnterScript` требуется соответствующий вызов этого метода.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)