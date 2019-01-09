---
title: IActiveScriptSiteDebug::GetRootApplicationNode | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40c837d5ee2e8b75bfe7603370d61385a67080cc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088521"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
Получает узел приложения, в области какой сценарий следует добавить документы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppdanRoot`  
 [out] Узел отладки приложения, который хранит документов скрипта. Может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает узел приложения, в котором должны быть добавлены документы скриптов. Этот метод может возвращать `NULL` для `ppdanRoot` Если документы скрипта должен быть верхнего уровня.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)