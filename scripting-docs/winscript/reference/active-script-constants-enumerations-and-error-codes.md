---
title: Активных скриптов константы, перечисления и коды ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090b494e904fbef1c0d3d8b380f7a184a6042788
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150950"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Константы, перечисления и коды ошибок активных скриптов
В этом разделе описываются перечисления и коды ошибок, используемые в обработчики сценариев Windows.  
  
## <a name="constants"></a>Константы  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константы SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Указывает тип потока.|  
  
## <a name="properties"></a>Свойства  
  
|Свойство|Описание:|  
|--------------|-----------------|  
|[Свойство SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Используется для указания ли обработчик скриптов должен сохраняться полнофункциональный, при наличии ссылки на медиафайл.|  
  
## <a name="enumerations"></a>Перечисления  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Тип, для выполнения сборки мусора.|  
|[Перечисление SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Задает возможные сценарии версии.|  
|[Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Задает состояние обработчика сценариев.|  
|||  
|[Перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Указывает состояние потока в обработчик сценариев.|  
|[Перечисление SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Представляет событие скрипта, отслеживаемого. Используется в [метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Представляет способ обработки элемента управления пользовательского интерфейса.|  
|[Перечисление SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Представляет тип элемента пользовательского интерфейса. Используется в [метод IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Коды ошибок  
  
|Код ошибки|Описание:|  
|----------------|-----------------|  
|[Код ошибки SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Ошибка сценария передается вызывающему объекту, который может находиться в другом потоке.|  
|[Код ошибки SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Ошибка прошло между обработчик скриптов и узлом.|  
|[Код ошибки SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Обработчик скриптов обнаружил необработанное исключение на узел.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)