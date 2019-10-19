---
title: 'Иактивескриптпроперти:: SetProperty | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571308"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Задает свойство, заданное параметром.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
  
 Значения, разрешенные для `dwProperty`, описаны в следующей таблице.  
  
|Константа|значения|Смысл|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Принудительное разделение обработчиком скриптов в режиме целых чисел вместо режима с плавающей точкой. Значение по умолчанию — `False`.|  
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
 Чтобы включить или отключить целочисленное деление, вызовите `SetProperty` и преобразуйте `Boolean` в `Object`. По умолчанию значение свойства равно `False`. Если задать для него значение `True`, операции деления будут возвращать только целые числа.  
  
 Чтобы включить или отключить пользовательское сравнение строк, вызовите `SetProperty` и передайте значение `Object`. Объект, передаваемый в, должен реализовывать [интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)интерфейса. Метод [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) интерфейса [IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) вызывается каждый раз при выполнении функции сравнения строк.  
  
 Чтобы выбрать набор языковых функций, которые должны поддерживаться при инициализации обработчика [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] скриптов, вызовите `SetProperty` и передайте значение, соответствующее набору функций языка, который должен быть включен для SCRIPTPROP_INVOKEVERSIONING. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступные языковые функции будут такими же, как и в версии 5,7 обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Если задано значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступны возможности языка, которые появились в версии 5,7 наряду с новыми функциями, добавленными в версии 5,8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), которое эквивалентно набору функций языка, который появился в версии 5,7, если узел не поддерживает другое поведение по умолчанию. Например, Internet Explorer 8 перемещается в функции языка [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которые поддерживаются обработчиком скриптов версии 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] по умолчанию, если режим документов по умолчанию для Internet Explorer 8 — режим "Internet Explorer 8 Standards". Переключение режима документов Internet Explorer 8 на режим "Стандартный" или "неограниченный" Internet Explorer 7 приводит к сбросу обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] для поддержки только набора функций языка, существовавшего в обработчике сценариев версии 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING следует устанавливать только при инициализации обработчика сценариев [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как заставить обработчик скриптов использовать деление целых чисел и как разрешить перегрузку функции Compare.  
  
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
 [Определение   совместимости документов](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [Иактивескриптпроперти](../../winscript/reference/iactivescriptproperty.md)    
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)