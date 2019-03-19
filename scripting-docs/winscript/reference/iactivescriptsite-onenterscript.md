---
title: IActiveScriptSite::OnEnterScript | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5505b30bbfd4e1cbc33022d38d7b7170ffd37dd3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150403"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Информирует узла о том, что обработчик скриптов началось выполнение кода скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Примечания  
 Этот метод необходимо вызвать обработчик скриптов при каждом входе или повторный вход в обработчик сценариев. Например, если скрипт вызывает объект, который затем запускает событие обработано обработчиком сценариев, обработчик скриптов должен вызвать `IActiveScriptSite::OnEnterScript` до выполнения события и необходимо вызвать [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) метод после выполнения события, но перед возвратом к объекту, инициировавший событие. Вызовы этого метода могут быть вложенными. При каждом вызове этого метода необходимо соответствующего вызова `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)