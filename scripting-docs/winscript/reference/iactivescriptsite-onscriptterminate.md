---
title: IActiveScriptSite::OnScriptTerminate | Документация Майкрософт
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992657"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Информирует узла о том, что сценарий завершения выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvarResult`  
 [in] Адрес переменной, который содержит результат выполнения скрипта, или `NULL` Если скрипт создает результат отсутствует.  
  
 `pexcepinfo`  
 [in] Адрес `EXCEPINFO` структуру, содержащую сведения об исключении, созданные после завершения сценария или `NULL` Если исключение не было создано.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` в случае успешного выполнения.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов вызывает этот метод перед вызовом [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) метод, с установленным флагом SCRIPTSTATE_INITIALIZED, завершения. Этот метод может использоваться для возврата состояния завершения и результаты на узел. Обратите внимание, что много языков скриптов, которые основаны на получение событий от узла, жизнь диапазонов, которые определяются приложением. В этом случае этот метод может никогда не вызывается.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)