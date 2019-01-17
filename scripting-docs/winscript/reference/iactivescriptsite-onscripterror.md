---
title: IActiveScriptSite::OnScriptError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088417"
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