---
title: 'Иактивескриптпроперти:: Property | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571413"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Возвращает свойство, заданное параметром.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwProperty`  
 Получаемое значение свойства.  
  
 `pvarIndex`  
 Не используется.  
  
 `pvarValue`  
 Значение свойства.  
  
 Значения, разрешенные для `dwProperty`, описаны в следующей таблице.  
  
|Константа|значения|Смысл|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Принудительное разделение обработчиком скриптов в режиме целых чисел вместо режима с плавающей точкой.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Позволяет заменить функцию сравнения строк обработчика скриптов.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Информирует обработчик скриптов о том, что для участия в глобальном объекте не существует других обработчиков скриптов.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Заставляет обработчик сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выбирать набор языковых функций, которые должны поддерживаться. Набор функций языка по умолчанию, поддерживаемых обработчиком сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], эквивалентен набору функций языка, который появился в версии 5,7 обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент является недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
  
## <a name="remarks"></a>Заметки  
 Узел может использовать свойство SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION для информирования обработчика сценариев о том, что для участия в глобальном объекте не существует других обработчиков скриптов. Например, Internet Explorer может информировать механизм [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] о том, что отображаемая страница содержит только скрипты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Таким же, только подсистема [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] может добавлять новые свойства в окно глобальных объектов, и для этого нет подсистемы Visual Basic Scripting Edition (VBScript). Обработчик может игнорировать этот флаг или использовать его для оптимизации управления новыми членами, добавляемыми в глобальный объект.  
  
 Узел может использовать свойство SCRIPTPROP_INVOKEVERSIONING, чтобы выбрать набор языковых функций, которые должны поддерживаться при запуске обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступные языковые функции будут такими же, как и в версии 5,7 обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Если задано значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступны возможности языка, которые появились в версии 5,7 наряду с функциями, добавленными в версии 5,8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), которое эквивалентно набору функций языка, который появился в версии 5,7, если узел не поддерживает другое поведение по умолчанию. Например, Internet Explorer 8 перемещается в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] языковых функций, поддерживаемых обработчиком сценариев версии 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], если режим документов для Internet Explorer 8 является режимом Internet Explorer 8 Standards.  
  
## <a name="see-also"></a>См. также  
 [Определение   совместимости документов](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [Иактивескриптпроперти](../../winscript/reference/iactivescriptproperty.md)    
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)