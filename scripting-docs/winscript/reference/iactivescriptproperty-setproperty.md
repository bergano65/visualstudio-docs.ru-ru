---
title: IActiveScriptProperty::SetProperty | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 186608bc56cf8b3649f5beeb1e3a301580ce44bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279288"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Задает свойство, которое задается параметром.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
#### <a name="parameters"></a>Параметры  
 `dwProperty`  
 Задаваемое значение свойства.  
  
 `pvarIndex`  
 Не используется.  
  
 `pvarValue`  
 Значение свойства.  
  
 Использовать значения `dwProperty` описаны в следующей таблице.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Заставляет обработчик сценариев разделение данных в режиме целое число вместо режима с плавающей точкой. Значение по умолчанию — `False`.|  
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
 Чтобы включить или отключить целочисленное деление, вызвать `SetProperty` и преобразовать `Boolean` для `Object`. По умолчанию является значение свойства `False`. Если задано значение `True`, операции деления вернет только целые числа.  
  
 Чтобы включить или отключить сравнение пользовательских строк, вызвать `SetProperty` и передайте `Object` значение. Объект, который передается в должен реализовывать интерфейс [интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) метод [интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) интерфейс вызывается при каждом выполнении функции сравнения строк.  
  
 Для выбора набора языковых функций, которые должны поддерживаться при [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инициализации обработчика сценариев, вызывают `SetProperty` и передать значение, которое соответствует наборе должны быть включены SCRIPTPROP_INVOKEVERSIONING функций языка. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступных языковых функций являются те, которые были доступны в версии 5.7 же [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов. Если он имеет значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступных языковых функций, которые были доступны в версии 5.7 помимо новых функций, которые были добавлены в версии 5.8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), что эквивалентно набор функций языка, которая появилась в версии 5.7, если узел поддерживает поведение по умолчанию. Например, Internet Explorer 8 opts в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] языковые компоненты, которые поддерживаются в версии 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов по умолчанию, если режим документов по умолчанию для Internet Explorer 8 — режим «Internet Explorer 8, стандартный режим». Переключение в режим документов Internet Explorer 8 в стандартный режим Internet Explorer 7 или в режиме совместимости сбрасывает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов, поддерживают только набор функций языка, существовали в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика скриптов.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING должно быть установлено только тогда, когда [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инициализируемого обработчика скриптов.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как заставить обработчик скриптов, используйте оператор целочисленного деления и том, как разрешить перегрузку функции сравнения.  
  
```c#  
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
  
## <a name="see-also"></a>См. также  
 [Определение совместимости документов](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty —](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)