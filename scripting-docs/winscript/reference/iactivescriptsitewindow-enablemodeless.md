---
title: IActiveScriptSiteWindow::EnableModeless | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724934"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
В результате узла включить или отключить его главного окна, а также любые безрежимные диалоговые окна.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fEnable`  
 [in] Флаг, который, если `TRUE`, включает главное окно и немодальные диалоговые окна или если `FALSE`, отключает их.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Этот метод идентичен методу `IOleInPlaceFrame::EnableModeless` метод.  
  
 Вызов этого метода могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)