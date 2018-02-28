---
title: "Iactivescriptsite — | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Реализуемых основным приложением для создания сайта для обработчика сценариев Windows. Как правило этот узел будет связан с контейнером все объекты, которые являются видимыми для сценария (например, элементы управления ActiveX). Как правило этот контейнер будет соответствовать документа или просматриваемую страницу. Microsoft Internet Explorer, например, создать контейнер для каждой страницы HTML, отображаемой. Каждый ActiveX элемента управления (или другой объект автоматизации), на странице и обработчик скриптов, было бы перечисляемую внутри этого контейнера.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Возвращает идентификатор языкового стандарта, которые узел использует для отображения элементов пользовательского интерфейса.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Получает сведения об элементе, который был добавлен модуль с помощью вызова [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Извлекает строки, определяемой узла, который уникально определяет текущую версию документа с точки зрения поставщика услуг размещения.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Вызывается после завершения выполнения скрипта.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Уведомляет узел об изменении состояния обработчика скриптов.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Уведомляет узел, выполнения произошла ошибка обработчик был запущен сценарий.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Уведомляет узел, обработчик сценариев начал выполнение кода скрипта.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Уведомляет основное приложение о возврате обработчик скриптов выполнять код скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)