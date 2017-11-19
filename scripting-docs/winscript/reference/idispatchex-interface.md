---
title: "Интерфейс IDispatchEx | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>Интерфейс IDispatchEx
`IDispatchEx`, расширение `IDispatch` интерфейса, соответствующие поддерживает функции динамическими языками, например языки сценариев. В этом разделе описываются `IDispatchEx` интерфейс, различия между `IDispatch` и `IDispatchEx`и основания для расширения. Предполагается, что читатели знакомы с `IDispatch` и иметь доступ к `IDispatch` документации.  
  
## <a name="remarks"></a>Примечания  
 `IDispatch`по существу был разработан для Microsoft Visual Basic. Основным ограничением `IDispatch` — что предполагает, что объекты, статические. Другими словами поскольку объекты не изменяются во время выполнения, сведения о типе можно полностью описать их во время компиляции. Динамические моделей во время выполнения, найденные в языках сценариев, таких как Visual Basic Scripting Edition (VBScript) и [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и объектные модели, такие как динамический HTML требуется более гибкий интерфейс.  
  
 `IDispatchEx`была разработана для предоставления всех служб `IDispatch` а также некоторые расширения, которые подходят для таких языков сценариев более динамических языков позднего связывания. Дополнительные возможности `IDispatchEx` помимо поддерживаемых `IDispatch` являются:  
  
-   Добавление новых элементов к объекту «(expando)» — использовать `GetDispID` с `fdexNameEnsure` флаг.  
  
-   Удаление членов объекта, используйте `DeleteMemberByName` или `DeleteMemberByDispID`.  
  
-   С учетом регистра диспетчеризации операций — использовать `fdexNameCaseSensitive` или `fdexNameCaseInsensitive`.  
  
-   Поиск члена с именем неявного — использовать `fdexNameImplicit`.  
  
-   Перечислить идентификаторы DISPID объекта — использовать `GetNextDispID`.  
  
-   Карты из DISPID имени элемента, используйте `GetMemberName`.  
  
-   Получить свойства объекта элементов — использовать `GetMemberProperties`.  
  
-   Вызов метода с `this` указателя — использовать `InvokeEx` с DISPATCH_METHOD.  
  
-   Разрешить браузеров, которые поддерживают концепцию пространства имен, чтобы получить имя пространства родительского объекта — использовать `GetNameSpaceParent`.  
  
 Объекты, поддерживающие `IDispatchEx` также могут поддерживать `IDispatch` для обеспечения обратной совместимости. Динамическая природа объектов, которые поддерживают `IDispatchEx` может повлиять на несколько `IDispatch` интерфейс этих объектов. Например `IDispatch` следующие допущения:  
  
-   Член и параметр DISPID должен оставаться постоянным в течение времени существования объекта. Это позволяет клиенту получить идентификаторы DISPID однократно и кэшировать их для дальнейшего использования.  
  
 Поскольку `IDispatchEx` допускает добавление и удаление элементов в наборе допустимые идентификаторы DISPID не меняются. Тем не менее `IDispatchEx` требует, что сопоставление имени DISPID и элементов не изменяются. Это означает, что если удаляется элемент:  
  
-   Идентификатор DISPID нельзя использовать повторно, пока не будет создан элемент с тем же именем.  
  
-   Идентификатор DISPID должен оставаться действительным для `GetNextDispID`.  
  
-   Идентификатор DISPID должен быть принят надлежащим образом по любому `IDispatch` или `IDispatchEx` методы — они должны распознавать элемент как удаленный и возвращать код соответствующее сообщение об ошибке (обычно DISP_E_MEMBERNOTFOUND или S_FALSE).  
  
## <a name="examples"></a>Примеры  
 Это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] код в функции test() делает следующее:  
  
-   Создает новый объект путем вызова `Object` конструктор и присваивает указатель на новый объект в переменной Obj.  
  
-   Создает новый элемент с именем Elem в объект и присваивает указатель на функцию cat этого элемента.  
  
-   Вызывает эту функцию. Так как он вызывается как метод, `this` указатель ссылается на объект Obj. Функция добавляет новый элемент, строки в объект.  
  
 Полный код HTML является:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Управления, размещаемым в этой же веб-странице может получить указатель диспетчеризации для обработчиков сценариев из браузера. Этот элемент управления может реализовывать затем test() функции:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Код из элемента управления, тестировать, то же, как [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функция `test()`. Обратите внимание, что эти вызовы dispatch были сделаны в работу [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ядра и изменять состояние ядра:  
  
-   Получает указатель диспетчеризации cat функции с помощью `GetDispID()`.  
  
-   Получает указатель диспетчеризации функция объекта с помощью `GetDispID()`.  
  
-   Создает объект путем вызова объекта функции `InvokeEx()` и получает указатель на вновь созданный объект диспетчеризации.  
  
-   Создает новый элемент, Elem, в объект с помощью `GetDispID()` с `fdexNameEnsure` флаг.  
  
-   Наведение указателя мыши диспетчеризации для cat в элемента с помощью `InvokeEx()`.  
  
-   Вызывает указатель диспетчеризации cat как метод путем вызова `InvokeEx()` и передача в указатель диспетчеризации на созданный объект как `this` указатель.  
  
-   Метод cat создает новый элемент в текущей строке `this` объекта.  
  
-   Проверяет, что новый элемент, линейчатые, созданные в сформированный объект перечисления в элементы с помощью `GetNextDispID()`.  
  
 Код для управления теста:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Методы  
 [Методы IDispatchEx](../../winscript/reference/idispatchex-methods.md)