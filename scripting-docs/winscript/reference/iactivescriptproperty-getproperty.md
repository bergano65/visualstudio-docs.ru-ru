---
title: IActiveScriptProperty::GetProperty | Документация Майкрософт
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
ms.openlocfilehash: e10d72e289fc2dc31464ce4505cea5c03e8d7f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992796"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Возвращает свойство, указанное в параметре.  
  
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
 Чтобы получить значение свойства.  
  
 `pvarIndex`  
 Не используется.  
  
 `pvarValue`  
 Значение свойства.  
  
 Использовать значения `dwProperty` описаны в следующей таблице.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Заставляет обработчик сценариев разделение данных в режиме целое число вместо режима с плавающей точкой.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Позволяет функции сравнения строки замены обработчика скриптов.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Информирует обработчик скриптов, на который нет других обработчиков сценариев, которые влияют на глобальный объект.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Заставляет [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов для выбора набора языковых функций, которые должны поддерживаться. По умолчанию набора языковых функций, поддерживаемых [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов эквивалентно набор функций языка, которая появилась в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент является недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 Узел можно использовать свойство SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION для информирования обработчик скриптов, который нет других обработчиков сценариев, которые влияют на глобальный объект. Например, Internet Explorer может сообщать [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] engine, который отображаемой странице содержит только [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] сценариев. Таким образом только [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ядра можно добавлять новые свойства в окне глобальный объект, и нет ни одному обработчику Visual Basic Scripting Edition (VBScript), делать то же самое. Ядро может игнорировать этот флаг или можно использовать его для оптимизации управления новых элементов, добавленных к глобальным объектом.  
  
 Узел может использовать свойство SCRIPTPROP_INVOKEVERSIONING для выбора набора возможностей языка, чтобы быть поддерживается при [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] работы обработчика скриптов. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступных языковых функций являются те, которые были доступны в версии 5.7 же [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов. Если он имеет значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступных языковых функций, которые были доступны в версии 5.7 наряду с возможностями, которые были добавлены в версии 5.8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), что эквивалентно набор функций языка, которая появилась в версии 5.7, если узел поддерживает поведение по умолчанию. Например, Internet Explorer 8 opts в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функции языка, поддерживаемые версии 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов по умолчанию, если режим документов для Internet Explorer 8 — режим «Internet Explorer 8, стандартный режим».  
  
## <a name="see-also"></a>См. также  
 [Определение совместимости документов](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty —](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)