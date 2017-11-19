---
title: "Активных скриптов константы, перечисления и коды ошибок | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Константы, перечисления и коды ошибок активных скриптов
В этом разделе описываются перечисления и коды ошибок, используемые в механизмах сценариев Windows.  
  
## <a name="constants"></a>Константы  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константы SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Указывает тип потока.|  
  
## <a name="properties"></a>Свойства  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Используется для указания ли обработчик скриптов должны храниться полнофункциональными, если нет ожидающих ссылок.|  
  
## <a name="enumerations"></a>Перечисления  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Тип, для выполнения сборки мусора.|  
|[Перечисление SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Указывает возможные сценарии версий.|  
|[Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Задает состояние обработчика сценариев.|  
|||  
|[Перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Указывает состояние потока в обработчик сценариев.|  
|[Перечисление SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Представляет событие скрипта, отслеживаемого. Используется в [метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Представляет способ обработки элемент управления пользовательского интерфейса.|  
|[Перечисление SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Представляет тип элемента пользовательского интерфейса. Используется в [метод IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Коды ошибок  
  
|Код ошибки|Описание|  
|----------------|-----------------|  
|[Код ошибки SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Ошибка сценария распространяется вызывающему объекту, который может находиться в другом потоке.|  
|[Код ошибки SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Ошибка прошло между обработчиком сценариев и узлом.|  
|[Код ошибки SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Обработчик скриптов обнаружил необрабатываемое исключение в узел.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)