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
ms.openlocfilehash: 673b3f1e64caa79dc2b21641209423d93fe0f834
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144419"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Предоставляет доступ к свойствам и методам, предоставляемым `IDispatchEx` объектом.  
  
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
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` для получения идентификатора диспетчеризации.  
  
 `lcid`  
 Контекст языкового стандарта, в котором следует интерпретировать аргументы. Передается в, `lcid` `InvokeEx` чтобы разрешить объекту интерпретировать свои аргументы, относящиеся к языковому стандарту.  
  
 `wFlags`  
 Допустимые значения для `wFlags` :  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Флаги, описывающие контекст `InvokeEx` вызова:  
  
|Значение|Значение|  
|-----------|-------------|  
|DISPATCH_METHOD|Член вызывается как метод. Если свойство имеет такое же имя, можно задать и это, и флаг DISPATCH_PROPERTYGET (определяется параметром `IDispatch` ).|  
|DISPATCH_PROPERTYGET|Элемент извлекается как свойство или элемент данных (определяется `IDispatch` ).|  
|DISPATCH_PROPERTYPUT|Элемент изменяется как свойство или элемент данных (определяется параметром `IDispatch` ).|  
|DISPATCH_PROPERTYPUTREF|Элемент изменяется ссылочным присваиванием, а не присваиванием значения. Этот флаг допустим, только если свойство принимает ссылку на объект (определенный параметром `IDispatch` ).|  
|DISPATCH_CONSTRUCT|Элемент используется в качестве конструктора. (Это новое значение, определенное в `IDispatchEx` ). Допустимые значения для `wFlags` :<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Указатель на структуру, содержащую массив аргументов, массив DISPID для именованных аргументов, а также счетчики количества элементов в массивах. `IDispatch`Полное описание структуры DISPPARAMS см. в документации.  
  
 `pVarRes`  
 Указатель на расположение, где будет храниться результат, или значение null, если вызывающий объект не ждет результата. Этот аргумент не учитывается, если указан DISPATCH_PROPERTYPUT или DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Указатель на структуру, содержащую сведения об исключении. Эта структура должна быть заполнена при `DISP_E_EXCEPTION` возвращении. Может иметь значение null. `IDispatch`Полное описание структуры см. в документации `EXCEPINFO` .  
  
 `pspCaller`  
 Указатель на объект поставщика услуг, предоставленный вызывающим объектом, который позволяет объекту получать службы от вызывающего. Может иметь значение null.  
  
 `IDispatchEx::InvokeEx`предоставляет все те же функции, что `IDispatch::Invoke` и, и добавляет несколько расширений:  
  
|Значение|Значение|
|-|-|  
|DISPATCH_CONSTRUCT|Указывает, что элемент используется в качестве конструктора.|  
|`pspCaller`|`pspCaller`Предоставляет объекту доступ к службам, предоставляемым вызывающим объектом. Конкретные службы могут обрабатываться самим вызывающим объектом или делегированы вызывающим объектам дальше по цепочке вызовов. Например, если обработчик скриптов в браузере вызывает `InvokeEx` внешний объект, объект может следовать за `pspCaller` цепочкой для получения служб из обработчика скриптов или браузера. (Обратите внимание, что цепочка вызовов отличается от цепочки создания, также известной как цепочка контейнеров или цепочка сайтов. Цепочка создания может быть доступна через какой-либо другой механизм, например `IObjectWithSite` .)|  
|Указатель `this`|Если DISPATCH_METHOD установлен в `wFlags` , для этого значения может существовать "именованный параметр". Идентификатор DISPID будет DISPID_THIS и должен быть первым именованным параметром.|  
  
 Неиспользованный `riid` параметр в `IDispatch::Invoke` был удален.  
  
 `puArgArr`Параметр в `IDispatch::Invoke` был удален.  
  
 См `IDispatch::Invoke` . документацию по следующим примерам.  
  
 "Вызов метода без аргументов"  
  
 "Получение и задание свойств"  
  
 "Передача параметров"  
  
 "Индексированные свойства"  
  
 "Вызов исключений во время вызова"  
  
 "Возвращение ошибок"  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|  
|-|-|  
|`S_OK`|Успех.|  
|DISP_E_BADPARAMCOUNT|Число элементов, предоставленных для DISPPARAMS, отличается от числа аргументов, принимаемых методом или свойством.|  
|DISP_E_BADVARTYPE|Один из аргументов в не является `rgvarg` допустимым типом Variant.|  
|DISP_E_EXCEPTION|Приложению необходимо вызвать исключение. В этом случае переданная структура `pei` должна быть заполнена.|  
|DISP_E_MEMBERNOTFOUND|Запрошенный элемент не существует, или вызов пытается `InvokeEx` установить значение свойства, доступного только для чтения.|  
|DISP_E_NONAMEDARGS|Эта реализация не `IDispatch` поддерживает именованные аргументы.|  
|DISP_E_OVERFLOW|Один из аргументов в `rgvarg` не удалось привести к указанному типу.|  
|DISP_E_PARAMNOTFOUND|Один из параметров DISPID не соответствует параметру метода.|  
|DISP_E_TYPEMISMATCH|Не удалось привести один или несколько аргументов.|  
|DISP_E_UNKNOWNLCID|Вызываемый член интерпретирует строковые аргументы в соответствии с кодом языка, а LCID не распознается. Если код языка (LCID) не необходим для интерпретации аргументов, то эта ошибка не возвращается.|  
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
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Жетдиспид](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)