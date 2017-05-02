---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty — метод, IActiveScriptProperty — интерфейс"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
Задает свойство, заданное параметром.  
  
## Синтаксис  
  
```  
HRESULT SetProperty(  
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
 Задаваемое значение свойства.  
  
 `pvarIndex`  
 Не используется.  
  
 `pvarValue`  
 Значение свойства.  
  
 Значения, разрешенные для `dwProperty` описаны в таблице ниже.  
  
|Константа|Значение|Значение|  
|---------------|--------------|--------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Заставляет обработчик скриптов для разбиения в режиме целого числа вместо режима с плавающей запятой.  Значение по умолчанию — `False`.|  
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
 Чтобы включить или отключить деление целого числа, вызовите `SetProperty` и convert `Boolean` к `Object`.  По умолчанию значение свойства `False`.  Если установлено в `True`, операции деления возвращает только целые числа.  
  
 Включить или отключить пользовательское сравнение строк, вызвать `SetProperty` и передать в значение `Object`.  Объект, который передается в должен реализовать интерфейс [Интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md).  Метод [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) интерфейса [Интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) вызова всякий раз, строка сравнивает функция исполнитьа.  
  
 Для выбора набора функций языка для поддержки при инициализации обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], вызовите `SetProperty` и передайте значение, которое соответствует набору функций языка, необходимый для SCRIPTPROP\_INVOKEVERSIONING.  Если это свойство установлено значение 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), доступных языковых функций совпадают, какие те, которые появились в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов.  Если он установлен в значение 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), то функции доступных языковых те, которые появились в версии 5.7 в дополнение к новым функциям, которые были добавитьы в версии 5.8.  По умолчанию это свойство установлено значение 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), которое эквивалентно set функции языка, которая отображается в версию 5.7, если основное приложение не будет поддерживать различие по умолчанию расширений функциональности.  Например, Internet Explorer 8 выбирает в функции языка [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которые поддерживаются по умолчанию обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] версии 5.8, когда режим документа по умолчанию для Internet Explorer 8 "режим стандартов Internet Explorer 8".  Переключение режима документа Internet Explorer 8 в режим стандартов или функциях Internet Explorer 7 сбросит обработчик скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] для поддержки только функция языка set, которая существовала в обработчике скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] версии 5.7.  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING должно быть установлено только при инициализации обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Пример  
 В следующем примере показано, как применять обработчик скриптов для использования деления целых числа и, как разрешить перегружать функцию сравнения.  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## См. также  
 [Определение совместимости документов](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)