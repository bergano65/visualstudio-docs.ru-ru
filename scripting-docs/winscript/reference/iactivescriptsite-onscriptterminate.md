---
title: IActiveScriptSite::OnScriptTerminate | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f8ff7c3d531b46fa6681776e79fbb73f6d1efca2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087117"
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