---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty — метод, IActiveScriptProperty — интерфейс"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
Возвращает свойство, заданное параметром.  
  
## Синтаксис  
  
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
  
#### Параметры  
 `dwProperty`  
 Значение возвращаемого свойства.  
  
 `pvarIndex`  
 Не используется.  
  
 `pvarValue`  
 Значение свойства.  
  
 Значения, разрешенные для `dwProperty` описаны в таблице ниже.  
  
|Константа|Значение|Значение|  
|---------------|--------------|--------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Заставляет обработчик скриптов для разбиения в режиме целого числа вместо режима с плавающей запятой.|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|Разрешает строка сравнение функции обработчика скриптов, который требуется заменить.|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|Уведомляет обработчик скриптов, что никакие другие обработчики сценариев не существуют в глобальный объект.|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|Заставляет обработчик скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] для выбора набора функций языка для поддержки.  По умолчанию набор функций языков, поддерживаемых [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчиком сценариев является эквивалентом функции языка установки, которая отображается в версию 5.7 обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент является недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\).|  
  
## Заметки  
 Основное приложение может использовать свойство SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION для оповещения обработчик скриптов, что никакие другие обработчики сценариев не существуют в глобальный объект.  Например, Internet Explorer может информировать обработчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], отображаемой, что страница содержит только скрипты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Таким образом, только обработчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] может добавлять новые свойства к глобальным окно объекта, и обработчик visual basic scripting edition \(VBScript\), чтобы сделать эти же.  Обработчик может пропустить этот пометить или может использовать его, чтобы оптимизировать управление новых элементов, добавитьы к глобальному объекту.  
  
 Основное приложение может использовать свойство SCRIPTPROP\_INVOKEVERSIONING для выбора набора функций языка для поддержки, когда обработчик скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] запуска.  Если это свойство установлено значение 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), доступных языковых функций совпадают, какие те, которые появились в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов.  Если он установлен в значение 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), то функции доступных языковых те, которые появились в версии 5.7 в дополнение к тем, которые были добавитьы в версии 5.8.  По умолчанию это свойство установлено значение 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), которое эквивалентно set функции языка, которая отображается в версию 5.7, если основное приложение не будет поддерживать различие по умолчанию расширений функциональности.  Например, 8 Internet Explorer выбирает в функции языка [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] поддерживаемые по умолчанию обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] версии 5.8, когда режим документа в Internet Explorer 8 "режим стандартов Internet Explorer 8".  
  
## См. также  
 [Определение совместимости документов](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)