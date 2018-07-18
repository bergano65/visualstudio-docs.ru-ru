---
title: Iactivescriptsitewindow — | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725134"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Этот интерфейс реализуется в узлах, поддерживающих интерфейс пользователя на один и тот же объект как [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) . Узлы, не поддерживающие пользовательского интерфейса, такие как серверы, не реализует `IActiveScriptSiteWindow` интерфейса. Обработчик скриптов обращается к этот интерфейс путем вызова `QueryInterface` из `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Возвращает дескриптор окна, может выступать в качестве владельца всплывающее окно, которое должно отображаться обработчика скриптов.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|В результате узла включить или отключить его главного окна, а также любые безрежимные диалоговые окна.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)