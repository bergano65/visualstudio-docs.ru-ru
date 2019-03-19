---
title: IActiveScriptSiteWindow::GetWindow | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b6efa066765339375a8315695aa9c1de2f9c46b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154248"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Получает дескриптор окна, которое может выступать в качестве владельца всплывающее окно, которое необходимо отобразить обработчика скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phwnd`  
 [out] Адрес переменной, которая получает дескриптор окна.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Этот метод аналогичен методу `IOleWindow::GetWindow` метод.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)