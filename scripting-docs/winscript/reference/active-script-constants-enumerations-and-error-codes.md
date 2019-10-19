---
title: Константы, перечисления и коды ошибок в активных скриптах | Документация Майкрософт
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
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572721"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Константы, перечисления и коды ошибок активных скриптов
В этом разделе описываются перечисления и коды ошибок, используемые в обработчиках сценариев Windows.  
  
## <a name="constants"></a>Константы  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константы SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Указывает тип потока.|  
  
## <a name="properties"></a>Свойства  
  
|свойство;|Описание|  
|--------------|-----------------|  
|[Свойство SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Используется, чтобы указать, должна ли подсистема скриптов сохраняться в полной функциональности, если имеются необработанные ссылки.|  
  
## <a name="enumerations"></a>Перечисления  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[Перечисление SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Тип выполняемой сборки мусора.|  
|[Перечисление SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Указывает возможные версии скриптов.|  
|[Перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Указывает состояние обработчика скриптов.|  
|||  
|[Перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Указывает состояние потока в обработчике скриптов.|  
|[Перечисление SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Представляет отслеживаемое событие скрипта. Используется в [методе метод iactivescriptsitetraceinfo:: SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Представляет способ обработки элемента управления пользовательского интерфейса.|  
|[Перечисление SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Представляет тип элемента пользовательского интерфейса. Используется в [методе иактивескриптситеуиконтрол:: жетуибехавиор](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Коды ошибок  
  
|Код ошибки|Описание|  
|----------------|-----------------|  
|[Код ошибки SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Ошибка скрипта распространяется на вызывающий объект, который может находиться в другом потоке.|  
|[Код ошибки SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Между обработчиком скриптов и узлом была передана ошибка.|  
|[Код ошибки SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Обработчик скриптов сообщил о необработанном исключении в узел.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)