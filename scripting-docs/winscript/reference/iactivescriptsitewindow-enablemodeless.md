---
title: IActiveScriptSiteWindow::EnableModeless | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4f15135273b98a65903a5d03de87c541fc032cce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992930"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
В результате узел для включения или отключения основного окна, а также любой немодальных диалоговых окон.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
  
 Вызовы этого метода могут быть вложенными.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)