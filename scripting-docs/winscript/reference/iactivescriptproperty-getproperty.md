---
title: "IActiveScriptProperty::GetProperty | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Возвращает свойство, которое указано в параметре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
  
 Допускаются значения для `dwProperty` описаны в следующей таблице.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Вызывает обработчик скриптов для разделения в целое число со знаком режиме вместо режима с плавающей точкой.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Позволяет функции сравнения строки замены обработчика сценариев.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Информирует о том, что нет других обработчиков сценариев, которые влияют на глобальный объект обработчика скриптов.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Принудительно начинает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов для выбора набора возможностей языка для поддержки. Набор функций языка, поддерживаемые по умолчанию [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов эквивалентно набор функций языка, которая появилась в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика сценариев.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент является недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 Узел может использовать свойство SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION для информирования обработчика скриптов, что нет других обработчиков сценариев, которые влияют на глобальный объект. Например, Internet Explorer может сообщать [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] engine, который готовится к просмотру страницы содержит только [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] сценариев. Таким образом только [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] engine можно добавлять новые свойства в окне глобальный объект, и нет ни одному обработчику Visual Basic Scripting Edition (VBScript) сделать то же самое. Обработчик можно пропустить этот флаг, или можно использовать его для оптимизации управления новых элементов, которые были добавлены с глобальным объектом.  
  
 Узел может использовать свойство SCRIPTPROP_INVOKEVERSIONING Выбор набора возможностей языка, чтобы быть поддерживаются, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] работы обработчика сценариев. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступные языковые возможности совпадают, появившиеся в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика сценариев. Если он имеет значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступные языковые функции, те, которые были доступны в версии 5.7 в дополнение к функциям, которые были добавлены в версии 5.8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), что эквивалентно набор функций языка, которая появилась в версии 5.7, если узел не поддерживает поведение по умолчанию. Например, Internet Explorer 8 переводит в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] возможности языка, поддерживаемые версией 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов по умолчанию, если документ для Internet Explorer 8 используется режим «Internet Explorer 8, стандартный режим».  
  
## <a name="see-also"></a>См. также  
 [Определение совместимости документов](http://msdn.microsoft.com/library/cc288325)   
 [Iactivescriptproperty —](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)