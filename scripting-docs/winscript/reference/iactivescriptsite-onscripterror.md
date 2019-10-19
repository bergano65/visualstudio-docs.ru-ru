---
title: 'IActiveScriptSite:: Онскриптеррор | Документация Майкрософт'
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
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570271"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Информирует узел о том, что произошла ошибка выполнения, когда модуль запускал скрипт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pase`  
 окне Адрес интерфейса [иактивескриптеррор](../../winscript/reference/iactivescripterror.md) объекта Error. Узел может использовать этот интерфейс для получения сведений об ошибке выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение, `S_OK`, если ошибка была правильно обработана, или код ошибки, определенный OLE.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)