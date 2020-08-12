---
title: IActiveScriptSite | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144666"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Реализуется узлом для создания сайта для обработчика сценариев Windows. Как правило, этот сайт будет связан с контейнером всех объектов, видимых для скрипта (например, элементов управления ActiveX). Как правило, этот контейнер будет соответствовать просматриваемому документу или странице. Например, Microsoft Internet Explorer создает такой контейнер для каждой отображаемой HTML-страницы. Каждый элемент управления ActiveX (или другой объект автоматизации) на странице, а также сам обработчик скриптов может быть перечислимым в этом контейнере.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Извлекает идентификатор локали, используемый узлом для отображения элементов пользовательского интерфейса.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Получает сведения об элементе, добавленном в обработчик с помощью вызова метода [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Извлекает определяемую узлом строку, уникально идентифицирующую текущую версию документа с точки зрения узла.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Вызывается после завершения выполнения скрипта.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Информирует узел о том, что состояние обработчика сценариев изменилось.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Информирует узел о том, что произошла ошибка выполнения, когда модуль запускал скрипт.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Информирует узел о том, что обработчик скриптов начал выполнение кода скрипта.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Информирует узел о том, что обработчик скриптов вернул выполнение кода скрипта.|  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)