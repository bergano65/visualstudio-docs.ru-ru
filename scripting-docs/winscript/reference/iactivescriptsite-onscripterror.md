---
title: IActiveScriptSite::OnScriptError | Документы Microsoft
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
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724634"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Уведомляет узел, выполнения произошла ошибка обработчик был запущен сценарий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pase`  
 [in] Адрес объекта error [iactivescripterror —](../../winscript/reference/iactivescripterror.md) интерфейса. Хост может использовать этот интерфейс для получения сведений об ошибке выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если ошибка была правильно обработана, а также OLE определенные код ошибки, в противном случае.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)