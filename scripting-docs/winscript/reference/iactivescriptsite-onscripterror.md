---
title: IActiveScriptSite::OnScriptError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147622"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Информирует узла о том, что выполнения произошла ошибка обработчик был запущен сценарий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pase`  
 [in] Адрес объекта error [iactivescripterror —](../../winscript/reference/iactivescripterror.md) интерфейс. Узел может использовать этот интерфейс для получения сведений об ошибке выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если ошибка была правильно обработана, или объект OLE определенный код ошибки, в противном случае.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)