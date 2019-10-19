---
title: 'IActiveScriptSite:: Онскрипттерминате | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570202"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Информирует узел о завершении выполнения скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvarResult`  
 окне Адрес переменной, содержащей результат скрипта, или `NULL`, если скрипт не выдал результатов.  
  
 `pexcepinfo`  
 окне Адрес структуры `EXCEPINFO`, которая содержит сведения об исключении, созданные при завершении скрипта, или `NULL`, если исключение не было создано.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Заметки  
 Обработчик скриптов вызывает этот метод перед вызовом метода [IActiveScriptSite:: онстатечанже](../../winscript/reference/iactivescriptsite-onstatechange.md) с установленным флагом SCRIPTSTATE_INITIALIZED. Этот метод можно использовать для возврата состояния завершения и результатов на узел. Обратите внимание, что многие языки сценариев, основанные на стоке событий с узла, имеют периоды жизни, определенные узлом. В этом случае этот метод не может быть вызван.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)