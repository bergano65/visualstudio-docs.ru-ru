---
title: 'IDispatchEx:: Инвокикс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575320"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Предоставляет доступ к свойствам и методам, предоставляемым объектом `IDispatchEx`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Для получения идентификатора диспетчеризации использует `GetDispID` или `GetNextDispID`.  
  
 `lcid`  
 Контекст языкового стандарта, в котором следует интерпретировать аргументы. @No__t_0 передается в `InvokeEx`, чтобы разрешить объекту интерпретировать свои аргументы, относящиеся к языковому стандарту.  
  
 `wFlags`  
 Допустимые значения для `wFlags`:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Флаги, описывающие контекст вызова `InvokeEx`:  
  
|значения|Смысл|  
|-----------|-------------|  
|DISPATCH_METHOD|Член вызывается как метод. Если свойство имеет такое же имя, можно задать и его, и флаг DISPATCH_PROPERTYGET (определяется `IDispatch`).|  
|DISPATCH_PROPERTYGET|Элемент извлекается как свойство или элемент данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Элемент изменяется как свойство или элемент данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Элемент изменяется ссылочным присваиванием, а не присваиванием значения. Этот флаг допустим, только если свойство принимает ссылку на объект (определяется `IDispatch`).|  
|DISPATCH_CONSTRUCT|Элемент используется в качестве конструктора. (Это новое значение, определенное `IDispatchEx`). Допустимые значения для `wFlags`:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Указатель на структуру, содержащую массив аргументов, массив DISPID для именованных аргументов, а также счетчики количества элементов в массивах. Полное описание структуры DISPPARAMS см. в документации по `IDispatch`.  
  
 `pVarRes`  
 Указатель на расположение, где будет храниться результат, или значение null, если вызывающий объект не ждет результата. Этот аргумент не учитывается, если указан DISPATCH_PROPERTYPUT или DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Указатель на структуру, содержащую сведения об исключении. Эта структура должна быть заполнена, если возвращается `DISP_E_EXCEPTION`. Может иметь значение null. Полное описание структуры `EXCEPINFO` см. в `IDispatch` документации.  
  
 `pspCaller`  
 Указатель на объект поставщика услуг, предоставленный вызывающим объектом, который позволяет объекту получать службы от вызывающего. Может иметь значение null.  
  
 `IDispatchEx::InvokeEx` предоставляет все те же функции, что и `IDispatch::Invoke`, и добавляет несколько расширений:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Указывает, что элемент используется в качестве конструктора.|  
|`pspCaller`|@No__t_0 предоставляет объекту доступ к службам, предоставляемым вызывающим объектом. Конкретные службы могут обрабатываться самим вызывающим объектом или делегированы вызывающим объектам дальше по цепочке вызовов. Например, если обработчик скриптов в браузере выполняет `InvokeEx` вызов к внешнему объекту, объект может следовать цепочке `pspCaller` для получения служб из обработчика скриптов или браузера. (Обратите внимание, что цепочка вызовов отличается от цепочки создания, также известной как цепочка контейнеров или цепочка сайтов. Цепочка создания может быть доступна через какой-либо другой механизм, например `IObjectWithSite`.)|  
|Указатель `this`|Если DISPATCH_METHOD задан в `wFlags`, для этого значения может существовать "именованный параметр". DISPID будет DISPID_THIS и должен быть первым именованным параметром.|  
  
 Неиспользуемый параметр `riid` в `IDispatch::Invoke` был удален.  
  
 Параметр `puArgArr` в `IDispatch::Invoke` был удален.  
  
 В следующих примерах см. документацию по `IDispatch::Invoke`.  
  
 "Вызов метода без аргументов"  
  
 "Получение и задание свойств"  
  
 "Передача параметров"  
  
 "Индексированные свойства"  
  
 "Вызов исключений во время вызова"  
  
 "Возвращение ошибок"  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|DISP_E_BADPARAMCOUNT|Число элементов, предоставленных для DISPPARAMS, отличается от числа аргументов, принимаемых методом или свойством.|  
|DISP_E_BADVARTYPE|Один из аргументов в `rgvarg` не является допустимым типом Variant.|  
|DISP_E_EXCEPTION|Приложению необходимо вызвать исключение. В этом случае структура, передаваемая в `pei`, должна быть заполнена.|  
|DISP_E_MEMBERNOTFOUND|Запрошенный элемент не существует, или при вызове `InvokeEx` попытка установить значение свойства, доступного только для чтения.|  
|DISP_E_NONAMEDARGS|Эта реализация `IDispatch` не поддерживает именованные аргументы.|  
|DISP_E_OVERFLOW|Один из аргументов в `rgvarg` не удалось привести к указанному типу.|  
|DISP_E_PARAMNOTFOUND|Один из параметров DISPID не соответствует параметру метода.|  
|DISP_E_TYPEMISMATCH|Не удалось привести один или несколько аргументов.|  
|DISP_E_UNKNOWNLCID|Вызываемый член интерпретирует строковые аргументы в соответствии с кодом языка, а LCID не распознается. Если код языка не требуется для интерпретации аргументов, эта ошибка не должна возвращаться.|  
|DISP_E_PARAMNOTOPTIONAL|Пропущен обязательный параметр.|  
  
## <a name="example"></a>Пример  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx:: жетдиспид](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)