---
title: 'IActiveScriptSite:: Онлеавескрипт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570328"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Информирует узел о том, что обработчик скриптов вернул выполнение кода скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Заметки  
 Обработчик скриптов должен вызвать этот метод перед возвратом управления вызывающему приложению, которое перешло в обработчик скриптов. Например, если скрипт вызывает объект, который затем вызывает событие, обработанное обработчиком скриптов, обработчик скриптов должен вызвать метод [IActiveScriptSite:: онентерскрипт](../../winscript/reference/iactivescriptsite-onenterscript.md) перед выполнением события и вызвать `IActiveScriptSite::OnLeaveScript` после выполнения события. перед возвращением в объект, который вызвал событие. Вызовы этого метода могут быть вложенными. Каждый вызов `IActiveScriptSite::OnEnterScript` требует соответствующего вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)