---
title: IActiveScriptSite::OnLeaveScript | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348299"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Информирует узел, что обработчик скриптов возвращаемому при выполнении кода скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Примечания  
 Этот метод необходимо вызвать обработчик сценариев перед возвратом управления вызывающему приложению, которое введено обработчика скриптов. Например, если скрипт вызывает объект, который затем запускает событие обработано обработчиком сценариев, обработчик скриптов должен вызвать [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) метод перед выполнением события и необходимо вызвать `IActiveScriptSite::OnLeaveScript`после выполнения события перед возвратом к объекту, инициировавший событие. Вызовы этого метода могут быть вложенными. При каждом вызове `IActiveScriptSite::OnEnterScript` требует соответствующего вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)