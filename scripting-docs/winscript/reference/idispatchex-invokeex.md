---
title: IDispatchEx::InvokeEx | Документация Майкрософт
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
ms.openlocfilehash: 33494836e463c9c2fd74acf7835d7e4630747b0e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157351"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Предоставляет доступ к свойствам и методам, предоставляемым `IDispatchEx` объекта.  
  
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
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` получить идентификатор диспетчеризации.  
  
 `lcid`  
 Контекст языкового стандарта, в котором следует интерпретировать аргументы. `lcid` Передается `InvokeEx` чтобы разрешить объект следует интерпретировать его аргументы, относящиеся к языковым стандартом.  
  
 `wFlags`  
 Допустимые значения для `wFlags` являются:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Флаги, описывающие контекст `InvokeEx` вызова:  
  
|Значение|Значение|  
|-----------|-------------|  
|DISPATCH_METHOD|Член вызывается как метод. Если свойство имеет то же имя, это и флаг DISPATCH_PROPERTYGET могут быть установлены (определяется `IDispatch`).|  
|DISPATCH_PROPERTYGET|Элемент извлекается в виде свойства или элемента данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Элемент изменяется как свойство или член данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Элемент изменяется путем присвоения ссылки, а не присвоения значения. Этот флаг допустим только в том случае, если свойство представляет ссылку на объект (определяемый `IDispatch`).|  
|DISPATCH_CONSTRUCT|Элемент используется в качестве конструктора. (Это новое значение определяется `IDispatchEx`). Допустимые значения для `wFlags` являются:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Указатель на структуру, содержащую массив аргументов, массив DISPID для именованных аргументов, а также счетчики количества элементов в массивах. См. в разделе `IDispatch` документации для полного описания структуры DISPPARAMS.  
  
 `pVarRes`  
 Указатель на местоположение, где должно храниться или значение Null, если вызывающий объект не ожидает результата результат. Этот аргумент учитывается, если указан DISPATCH_PROPERTYPUT или DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Указатель на структуру, содержащую сведения об исключении. Эта структура должно быть заполнено if `DISP_E_EXCEPTION` возвращается. Может иметь значение Null. См. в разделе `IDispatch` документации для полного описания `EXCEPINFO` структуры.  
  
 `pspCaller`  
 Указатель на объект поставщика служб, предоставляемые вызывающим объектом, позволяющий для получения служб от вызывающего объекта. Может иметь значение Null.  
  
 `IDispatchEx::InvokeEx` предоставляет все те же функции, что `IDispatch::Invoke` и добавляет несколько расширений:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Указывает, что элемент используется в качестве конструктора.|  
|`pspCaller`|`pspCaller` Позволяет доступа к объектам в службы, предоставляемые вызывающим объектом. Определенных служб может быть обработаны вызывающим сам или делегированные вызывающим объектам дальнейшей вверх по цепи вызова. Например, если обработчик скриптов в браузере делает `InvokeEx` можно выполнить вызов к внешнему объекту, объект `pspCaller` цепочки для получения служб из обработчика сценариев или браузера. (Обратите внимание, что цепочке вызовов не так же, как создание цепочки, также известное как цепочку контейнера или цепочки сайта. Создание цепочки могут быть доступны через другой механизм такие как `IObjectWithSite`.)|  
|Указатель `this`|Если имеет значение DISPATCH_METHOD `wFlags`, может быть «именованный параметр» для значения «this». Идентификатор DISPID будет DISPID_THIS, и он должен быть первый именованного параметра.|  
  
 Неиспользуемые `riid` параметр в `IDispatch::Invoke` был удален.  
  
 `puArgArr` Параметр в `IDispatch::Invoke` был удален.  
  
 См. в разделе `IDispatch::Invoke` документацию по приведенным ниже:  
  
 «Вызов метода без аргументов»  
  
 «Получение и задание свойств»  
  
 «Передача параметров»  
  
 «Индексированного свойства»  
  
 «Создание исключений во время вызова»  
  
 «Возвращение ошибки»  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|DISP_E_BADPARAMCOUNT|Количество элементов, предоставленных DISPPARAMS отличается от числа аргументов в объявлении метода или свойства.|  
|DISP_E_BADVARTYPE|Один из аргументов в `rgvarg` не является допустимым типом variant.|  
|DISP_E_EXCEPTION|Приложение должно вызвать исключение. В этом случае со структурой, переданной в `pei` должно быть заполнено.|  
|DISP_E_MEMBERNOTFOUND|Запрошенный элемент не существует, или вызов `InvokeEx` попытка задать значение свойства только для чтения.|  
|DISP_E_NONAMEDARGS|Эта реализация `IDispatch` не поддерживает именованные аргументы.|  
|DISP_E_OVERFLOW|Один из аргументов в `rgvarg` не может быть преобразовано в указанный тип.|  
|DISP_E_PARAMNOTFOUND|Один из параметров идентификаторов DispId не соответствует параметру метода.|  
|DISP_E_TYPEMISMATCH|Один или несколько аргументов были недопустимы.|  
|DISP_E_UNKNOWNLCID|Вызываемого члена интерпретирует строковых аргументов в соответствии с LCID, и код языка не распознан. Если код языка не требуется для интерпретации аргументов, эта ошибка не должно быть возвращено.|  
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
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)