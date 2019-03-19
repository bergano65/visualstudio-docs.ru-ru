---
title: IActiveScriptSiteWindow | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3691a874121c00dcccc69958eb5746a2c1d78122
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149462"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Этот интерфейс реализуется узлов, которые поддерживают пользовательский интерфейс на один и тот же объект как [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Узлы, которые не поддерживают пользовательского интерфейса, такие как серверы, не реализует `IActiveScriptSiteWindow` интерфейс. Обработчик скриптов обращается к этот интерфейс путем вызова `QueryInterface` из `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Извлекает дескриптор окна, который может выступать в качестве владельца всплывающее окно, которое необходимо отобразить обработчика скриптов.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|В результате узел для включения или отключения основного окна, а также любой немодальных диалоговых окон.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)