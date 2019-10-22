---
title: Иактивескриптситевиндов | Документация Майкрософт
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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575897"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Этот интерфейс реализуется узлами, которые поддерживают пользовательский интерфейс для того же объекта, что и [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Узлы, которые не поддерживают пользовательский интерфейс, такие как серверы, не реализуют интерфейс `IActiveScriptSiteWindow`. Обработчик скриптов обращается к этому интерфейсу, вызывая `QueryInterface` из `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Извлекает дескриптор окна, который может использоваться в качестве владельца всплывающего окна, которое должен отображать обработчик сценариев.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Заставляет узел включать или отключать его главное окно, а также любые немодальные диалоговые окна.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)