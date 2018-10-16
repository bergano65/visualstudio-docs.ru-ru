---
title: IDispatchEx::InvokeEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24730084"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Предоставляет доступ к свойствам и методам, предоставляемым `IDispatchEx` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` для получения идентификатора диспетчеризации.  
  
 `lcid`  
 Контекст языкового стандарта, в котором следует интерпретировать аргументы. `lcid` Передается `InvokeEx` чтобы объект следует интерпретировать его аргументы, связанные с языковым стандартом.  
  
 `wFlags`  
 Допустимые значения для `wFlags` являются:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Флаги, описывающие контекст `InvokeEx` вызова:  
  
|Значение|Значение|  
|-----------|-------------|  
|DISPATCH_METHOD|-Член вызывается как метод. Если свойство имеет то же имя, это и флаг DISPATCH_PROPERTYGET могут быть заданы (определяется `IDispatch`).|  
|DISPATCH_PROPERTYGET|Член извлекается как свойство или член данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Элемент изменяется как свойство или член данных (определяется `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Элемент изменяется путем присвоения ссылки, а не присвоения значения. Этот флаг действителен только в том случае, если свойство представляет собой ссылку на объект (определяемый `IDispatch`).|  
|DISPATCH_CONSTRUCT|Элемент используется как конструктор. (Это новое значение, определяемое `IDispatchEx`). Допустимые значения для `wFlags` являются:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Указатель на структуру, содержащую массив аргументов, массив DISPID для именованных аргументов, а также счетчики количества элементов в массивах. В разделе `IDispatch` документации полное описание структуры DISPPARAMS.  
  
 `pVarRes`  
 Указатель на расположение, где результат — должно храниться или значение Null, если вызывающий объект ожидает никаких результатов. Данный аргумент учитывается, если указан DISPATCH_PROPERTYPUT или DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Указатель на структуру, содержащую сведения об исключении. Эта структура должно быть заполнено if `DISP_E_EXCEPTION` возвращается. Может иметь значение Null. В разделе `IDispatch` документации для полного описания `EXCEPINFO` структуры.  
  
 `pspCaller`  
 Указатель на объект поставщика служб, предоставляемые вызывающим объектом, который разрешает объекту для получения служб от вызывающего объекта. Может иметь значение Null.  
  
 `IDispatchEx::InvokeEx`предоставляет все те же возможности, как `IDispatch::Invoke` и добавляет несколько расширений:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Указывает, что элемент используется в качестве конструктора.|  
|`pspCaller`|`pspCaller` Разрешает доступ объекта службы, предоставляемые вызывающим объектом. Определенных служб может обработаны вызывающим сам или делегировать вызывающим объектам дальнейшей в цепочке вызовов. Например, если обработчик скриптов в браузере делает `InvokeEx` можно выполнить вызов внешнего объекта, объект `pspCaller` цепочки для получения служб от обработчика сценариев или браузер. (Обратите внимание, что цепочки вызовов не совпадает с создания цепочки, также известное как цепочка контейнера или цепочки сайта. Создание цепочки например могут быть доступны в другой механизм `IObjectWithSite`.)|  
|Указатель `this`|Если задано DISPATCH_METHOD `wFlags`, может быть «именованный параметр» для значения «this». Идентификатор DISPID будет DISPID_THIS, и он должен быть именем первого параметра.|  
  
 Неиспользуемые `riid` параметр в `IDispatch::Invoke` был удален.  
  
 `puArgArr` Параметр в `IDispatch::Invoke` был удален.  
  
 В разделе `IDispatch::Invoke` документацию в следующих примерах:  
  
 «Вызов метода без аргументов»  
  
 «Получение и задание свойств»  
  
 «Передача параметров»  
  
 «Индексированных свойств»  
  
 «Создание исключений во время вызова»  
  
 «Возвращение ошибок»  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|DISP_E_BADPARAMCOUNT|Число элементов, предоставляемых в DISPPARAMS отличается от числа аргументов в объявлении метода или свойства.|  
|DISP_E_BADVARTYPE|Один из аргументов в `rgvarg` не является допустимым типом variant.|  
|DISP_E_EXCEPTION|Приложение должно вызвать исключение. В этом случае со структурой, переданной в `pei` должно быть заполнено.|  
|DISP_E_MEMBERNOTFOUND|Запрошенный элемент не существует, или вызов `InvokeEx` попытка задать значение свойства только для чтения.|  
|DISP_E_NONAMEDARGS|Эта реализация `IDispatch` не поддерживает именованные аргументы.|  
|DISP_E_OVERFLOW|Один из аргументов в `rgvarg` не может быть преобразовано в указанный тип.|  
|DISP_E_PARAMNOTFOUND|Один из параметров DISPID соответствует параметра в методе.|  
|DISP_E_TYPEMISMATCH|Один или несколько аргументов не может быть преобразовано.|  
|DISP_E_UNKNOWNLCID|Интерпретирует строковых аргументов в соответствии с LCID, и код языка не распознан. Если код языка не требуется для интерпретации аргументов, эта ошибка не должно быть возвращено.|  
|DISP_E_PARAMNOTOPTIONAL|Пропущен обязательный параметр.|  
  
## <a name="example"></a>Пример  
  
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
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)