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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992557"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Реализовано узлом для создания сайта для обработчика сценариев Windows. Как правило этот сайт будет связан с контейнером всех объектов, видимых в сценарий (например, элементы управления ActiveX). Как правило этот контейнер будет соответствовать просматриваемую страницу или документ. Microsoft Internet Explorer, например, создать контейнер для каждой отображаемой странице HTML. Каждый ActiveX элемента управления (или другой объект автоматизации), на странице и обработчик скриптов, будет перечисляемый внутри этого контейнера.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Извлекает идентификатор языкового стандарта, используемый узлом для отображения элементов пользовательского интерфейса.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Получает сведения об элементе, который был добавлен в обработчик посредством вызова [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Извлекает строку, однозначно определяющее текущую версию документа с точки зрения главного приложения определяемого узла.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Вызывается после завершения выполнения скрипта.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Уведомляет узел об изменении состояния обработчика скриптов.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Информирует узла о том, что выполнения произошла ошибка обработчик был запущен сценарий.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Информирует узла о том, что обработчик скриптов началось выполнение кода скрипта.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Информирует узел, что обработчик скриптов возвращаемому при выполнении кода скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)