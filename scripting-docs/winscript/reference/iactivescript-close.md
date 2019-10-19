---
title: 'IActiveScript:: Close | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575783"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Заставляет обработчик скриптов отменять любой загруженный скрипт, терять его состояние и освобождать все указатели интерфейса, которые он имеет, на другие объекты, тем самым выполняя вход в закрытое состояние. Приемники событий, немедленно исполняемый текст сценария и вызовы макросов, которые уже выполняются, выполняются до изменения состояния (используйте [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) для отмены выполняющегося потока сценария). Этот метод должен вызываться созданием узла перед освобождением интерфейса для предотвращения проблем с циклическими ссылками.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|значения|Смысл|  
|-----------|-------------|  
|`S_OK`|Выполнено.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов уже находится в закрытом состоянии).|  
|`OLESCRIPT_S_PENDING`|Метод был успешно поставлен в очередь, но состояние еще не изменилось. При изменении состояния сайт необходимо вызвать обратно в метод [IActiveScriptSite:: онстатечанже](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Метод выполнен успешно, но скрипт уже закрыт.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)