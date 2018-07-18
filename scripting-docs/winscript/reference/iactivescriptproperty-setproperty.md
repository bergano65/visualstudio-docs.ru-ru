---
title: IActiveScriptProperty::SetProperty | Документы Microsoft
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
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726504"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Задает свойство, которое указано в параметре.  
  
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
  
 Допускаются значения для `dwProperty` описаны в следующей таблице.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Вызывает обработчик скриптов для разделения в целое число со знаком режиме вместо режима с плавающей точкой. Значение по умолчанию — `False`.|  
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
 Чтобы включить или отключить целочисленное деление, вызовите `SetProperty` и преобразовать `Boolean` для `Object`. По умолчанию является значение свойства `False`. Если задано значение `True`, операции деления вернет только целые числа.  
  
 Чтобы включить или отключить сравнение пользовательских строк, вызвать `SetProperty` и передайте `Object` значение. Объект, который можно передавать должен реализовывать интерфейс [iactivescriptstringcompare — интерфейс](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) метод [iactivescriptstringcompare — интерфейс](../../winscript/reference/iactivescriptstringcompare-interface.md) интерфейс вызывается каждый раз при выполнении функции сравнения строк.  
  
 Выбор набора возможностей языка для поддержки при [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инициализации обработчика сценариев, вызывают `SetProperty` и передать значение, соответствующее значение для включения SCRIPTPROP_INVOKEVERSIONING функции языка. Если это свойство имеет значение 1 (SCRIPTLANGUAGEVERSION_5_7), доступные языковые возможности совпадают, появившиеся в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика сценариев. Если он имеет значение 2 (SCRIPTLANGUAGEVERSION_5_8), доступные языковые функции, те, которые были доступны в версии 5.7 помимо новых функций, которые были добавлены в версии 5.8. По умолчанию это свойство имеет значение 0 (SCRIPTLANGUAGEVERSION_DEFAULT), что эквивалентно набор функций языка, которая появилась в версии 5.7, если узел не поддерживает поведение по умолчанию. Например, Internet Explorer 8 переводит в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] возможностей языка, которые поддерживаются версией 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов по умолчанию, если режим документов по умолчанию для Internet Explorer 8 — режим «Internet Explorer 8, стандартный режим». Переключение в режим документов Internet Explorer 8, в стандартный режим Internet Explorer 7 или в режиме совместимости сбрасывает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчик скриптов для поддержки только набор функций языка, существовали в версии 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обработчика сценариев.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING должно быть установлено только тогда, когда [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инициализации обработчика сценариев.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как заставить обработчик скриптов для использования целочисленное деление и как разрешить перегрузку функции сравнения.  
  
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
 [Определение совместимости документов](http://msdn.microsoft.com/library/cc288325)   
 [Iactivescriptproperty —](../../winscript/reference/iactivescriptproperty.md)   
 [Сведения о версии](../../javascript/reference/javascript-version-information.md)