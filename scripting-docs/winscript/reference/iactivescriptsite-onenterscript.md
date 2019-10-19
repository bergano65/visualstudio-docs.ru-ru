---
title: 'IActiveScriptSite:: Онентерскрипт | Документация Майкрософт'
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
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570361"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Информирует узел о том, что обработчик скриптов начал выполнение кода скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Заметки  
 Обработчик скриптов должен вызывать этот метод при каждой записи или перезаписи в обработчик скриптов. Например, если скрипт вызывает объект, который затем вызывает событие, обработанное обработчиком скриптов, обработчик скриптов должен вызвать `IActiveScriptSite::OnEnterScript` перед выполнением события и вызвать метод [IActiveScriptSite:: онлеавескрипт](../../winscript/reference/iactivescriptsite-onleavescript.md) после выполнения события. но перед возвращением в объект, который вызвал событие. Вызовы этого метода могут быть вложенными. При каждом вызове этого метода требуется соответствующий вызов `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)