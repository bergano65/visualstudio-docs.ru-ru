---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx — метод"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
Предоставляет доступ к свойствам и методам, предоставляемым объектом `IDispatchEx`.  
  
## Синтаксис  
  
```  
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
  
#### Параметры  
 `id`  
 Идентифицирует член.  Использование `GetDispID` или `GetNextDispID` получить идентификатор диспетчера.  
  
 `lcid`  
 Контекст языкового стандарта, в котором следует интерпретировать аргументы.  `lcid` передается `InvokeEx` для разрешения объекта, чтобы интерпретировать ее аргументы, относящиеся к языковому стандарту.  
  
 `wFlags`  
 Допустимые значения для `wFlags`:  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 Флаги, описывающий контекст вызова `InvokeEx`:  
  
|Значение|Значение|  
|--------------|--------------|  
|DISPATCH\_METHOD|Член вызывается как метод.  Если свойство имеет то же имя, что и пометить DISPATCH\_PROPERTYGET может быть установлен \(distinct `IDispatch`\).|  
|DISPATCH\_PROPERTYGET|Элемент получить как свойство или элемент данных \(определяются `IDispatch`\).|  
|DISPATCH\_PROPERTYPUT|Элемент как свойство или изменить элемент данных \(определяются `IDispatch`\).|  
|DISPATCH\_PROPERTYPUTREF|Элемент изменения назначением ссылки, а не назначением значений.  Этот пометить допустим только в том случае, если свойство принимает ссылку на объект \(указанному `IDispatch`\).|  
|DISPATCH\_CONSTRUCT|Член используется как конструктор.  \(Это новое значение указанного `IDispatchEx`\).  Допустимые значения для `wFlags`:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 Указатель на структуру, содержащую массив аргументов, массив DISPID для именованных аргументов, а также счетчики количества элементов в массивах.  См. документацию `IDispatch` для полного описания структуры DISPPARAMS.  
  
 `pVarRes`  
 Указатель на место, где результат быть сохраненные или значение null, если вызывающий объект не ожидает никаких результатов.  Этот аргумент, если DISPATCH\_PROPERTYPUT или игнорировать DISPATCH\_PROPERTYPUTREF определены.  
  
 `pei`  
 Указатель на структуру, содержащую сведения об исключении.  Эта структура должна быть заполняемую при `DISP_E_EXCEPTION` возвращается.  Может принимать значение null.  См. документацию `IDispatch` для полного описания структуры `EXCEPINFO`.  
  
 `pspCaller`  
 Указатель на объект поставщика служб, предоставленный вызывающим объектом, который позволяет объекту получать службы от вызывающего объекта.  Может принимать значение null.  
  
 `IDispatchEx::InvokeEx` предоставляет те же функции, такие как `IDispatch::Invoke` и добавляет несколько расширений:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|Указывает, что элемент используется как конструктор.|  
|`pspCaller`|Обеспечивает доступ к службам `pspCaller` объекта предоставленного вызывающим объектом.  Определенные типы обслуживания могут быть обращаны самим или вызывающим объектом делегированы по вызову далее по цепочке вызова.  Например, если обработчик скриптов внутри браузера совершает к внешним `InvokeEx` объекта, то объект может следовать цепочкой `pspCaller` для получения служб из обработчика или обозревателя скриптов.  \(Следует отметить, цепочка вызовов не то же, что и цепочка \- создания известная также как цепочка контейнера или цепь сайта.  Цепочка создания может быть доступна через некоторый другой механизм, как `IObjectWithSite`\).|  
|Указатель `this`|При DISPATCH\_METHOD помещенные в `wFlags`, могут быть "параметр", "этого" значения.  Идентификатор DISPID будет DISPID\_THIS и должен быть первым именованным параметром.|  
  
 Неиспользуемый параметр `riid` в `IDispatch::Invoke` был удален.  
  
 Параметр `puArgArr` в `IDispatch::Invoke` был удален.  
  
 См. документацию `IDispatch::Invoke` в следующих примерах:  
  
 "Вызов метода без аргументов"  
  
 "Получение и установка свойства"  
  
 "Передача параметров"  
  
 Индексировал "свойства"  
  
 "Вызов исключения во время вызывают"  
  
 "Возвращение ошибок"  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|DISP\_E\_BADPARAMCOUNT|Число элементов, реализованных DISPPARAMS количество аргументов, принимаемых от методом или свойством.|  
|DISP\_E\_BADVARTYPE|Один из аргументов в `rgvarg` не является допустимым другого типа.|  
|DISP\_E\_EXCEPTION|Приложение должно вызвать исключение.  В этом случае структура, переданная в `pei` должна быть заполнена.|  
|DISP\_E\_MEMBERNOTFOUND|Запрошенный элемент не существует или вызов `InvokeEx` предпринял попытку установить значение свойства только для чтения.|  
|DISP\_E\_NONAMEDARGS|Эта реализация `IDispatch` не поддерживает именованные аргументы.|  
|DISP\_E\_OVERFLOW|Один из аргументов в `rgvarg` не удалось привести к указанному типу.|  
|DISP\_E\_PARAMNOTFOUND|Один из параметров идентификаторов dispid не соответствует параметру на методе.|  
|DISP\_E\_TYPEMISMATCH|Один или несколько аргументов не удалось приводится.|  
|DISP\_E\_UNKNOWNLCID|Аргументы вызываемого члена интерпретирует код языка и строки в соответствии с кодом языка не распознан.  Если код языка \(LCID\) не необходим для интерпретации аргументов, то эта ошибка не возвращается.|  
|DISP\_E\_PARAMNOTOPTIONAL|Обязательный параметр не указывается.|  
  
## Пример  
  
```  
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
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)