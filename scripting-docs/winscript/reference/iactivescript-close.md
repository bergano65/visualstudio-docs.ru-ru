---
title: IActiveScript::Close | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640974"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Вызывает обработчик скриптов для прерывания любой сценарий, текущая загруженная, теряют свое состояние и освободить все указатели на интерфейс, он имеет другим объектам, таким образом, введя состояние closed. Приемники событий, немедленно выполненный скрипт текст и вызовов макросов, которые уже были завершены до изменения состояния (используйте [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) отменить выполняющийся поток сценария). Этот метод должен вызываться создание приложением перед интерфейс освобождается для предотвращения проблем циклическую ссылку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|`S_OK`|Выполнено.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев уже был закрыт).|  
|`OLESCRIPT_S_PENDING`|Метод в очередь и успешно, но состояние еще не изменилась. Когда об изменении состояния сайта должна быть обратного вызова в [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) метод.|  
|`S_FALSE`|Метод успешно выполнен, но скрипт уже был закрыт.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)