---
title: "Константы, перечисления и коды ошибок активных скриптов | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Константы, перечисления и коды ошибок активных скриптов
Этот раздел описывает перечисления и коды ошибки, используемые в обработчиках скриптов Windows.  
  
## Константы  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константы SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Указывает тип потока.|  
  
## Свойства  
  
|Свойство.|Описание|  
|---------------|--------------|  
|[Свойство SCRIPTPROP\_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Используемый, чтобы определить, должен ли обработчик скриптов быть быть полностью функциональную, если необработанные ссылки.|  
  
## Перечисления  
  
|Перечисление|Описание|  
|------------------|--------------|  
|[Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Тип сборки мусора.|  
|[Перечисление SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Задает возможные сценарии версии.|  
|[Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Указывает состояние обработчика скриптов.|  
|||  
|[Перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Задает состояние потока в обработчике скриптов.|  
|[Перечисление SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Представляет событие скрипта, трассируется.  Используемый в [Метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Представляет способ, элемент управления пользовательского интерфейса, должно быть обращано.|  
|[Перечисление SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Представляет тип элемента пользовательского интерфейса.  Используемый в [Метод IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## Коды ошибок  
  
|Код ошибки|Описание|  
|----------------|--------------|  
|[Код ошибки SCRIPT\_E\_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Ошибка скрипта передачи вызывающему объекту, который может находиться в другом потоке.|  
|[Код ошибки SCRIPT\_E\_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Ошибка передается между обработчиком скрипта и основным приложением.|  
|[Код ошибки SCRIPT\_E\_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Обработчик скриптов сообщал необработанное исключение в основное приложение.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)