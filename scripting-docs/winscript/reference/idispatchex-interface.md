---
title: Интерфейс IDispatchEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22ccc54dee335fd8c81343557d2f32c48eb30560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837923"
---
# <a name="idispatchex-interface"></a>Интерфейс IDispatchEx
`IDispatchEx`, расширение `IDispatch` интерфейс, поддерживает функции, требуемым для динамических языков, таких как языки сценариев. В этом разделе описываются `IDispatchEx` интерфейс, различия между `IDispatch` и `IDispatchEx`и обоснование для расширений. Предполагается, что читатели знакомы с `IDispatch` и иметь доступ к `IDispatch` документации.  
  
## <a name="remarks"></a>Примечания  
 `IDispatch` по существу была разработана для Microsoft Visual Basic. Основным ограничением из `IDispatch` — что она предполагает, что объекты являются статическими. Другими словами поскольку объекты не изменяются во время выполнения, сведения о типе можно полностью описать их во время компиляции. Динамические моделей во время выполнения, найденные в языках сценариев, таких как Visual Basic Scripting Edition (VBScript) и [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и объектные модели, такие как динамический HTML требуется более гибкий интерфейс.  
  
 `IDispatchEx` был разработан для предоставления всех служб `IDispatch` а также некоторые расширения, соответствующие более динамических языков с поздним связыванием, таких как языки сценариев. Дополнительные возможности `IDispatchEx` рамки возможностей `IDispatch` являются:  
  
- Добавление новых элементов в объект («expando») — использовать `GetDispID` с `fdexNameEnsure` флаг.  
  
- Удаление членов объекта, используйте `DeleteMemberByName` или `DeleteMemberByDispID`.  
  
- С учетом регистра диспетчеризации операции — использовать `fdexNameCaseSensitive` или `fdexNameCaseInsensitive`.  
  
- Поиск члена с именем неявного — использовать `fdexNameImplicit`.  
  
- Перечислить идентификаторы DISPID объекта — использовать `GetNextDispID`.  
  
- Сопоставление DISPID имя элемента — использовать `GetMemberName`.  
  
- Получить свойства членов объектов — использовать `GetMemberProperties`.  
  
- Вызов метода с `this` указатель — использовать `InvokeEx` с DISPATCH_METHOD.  
  
- Разрешить браузеры, поддерживающие концепция пространства имен, чтобы получить имя пространство родительского объекта, используйте `GetNameSpaceParent`.  
  
  Объекты, поддерживающие `IDispatchEx` также можно включить поддержку `IDispatch` для обеспечения обратной совместимости. Динамическая природа объектов, которые поддерживают `IDispatchEx` есть несколько последствий для `IDispatch` интерфейс этих объектов. Например `IDispatch` следующие допущения:  
  
- Член и параметр DISPID должна оставаться постоянной в течение времени существования объекта. Это позволяет клиенту получить идентификаторы DISPID однократно и кэшировать их для последующего использования.  
  
  Так как `IDispatchEx` допускает добавление и удаление элементов, набор допустимых идентификаторов DispId не меняются. Тем не менее `IDispatchEx` требует, что сопоставление между DISPID и имени члена не изменяются. Это означает, что если удаляется элемент:  
  
- Идентификатор DISPID нельзя использовать повторно, пока не будет создан элемент с тем же именем.  
  
- Идентификатор DISPID должны оставаться допустимыми для `GetNextDispID`.  
  
- Идентификатор DISPID должен быть принят корректно по любому `IDispatch` или `IDispatchEx` методы — они должны распознавать элемент как удаленный и возврата соответствующего кода ошибки (обычно DISP_E_MEMBERNOTFOUND или S_FALSE).  
  
## <a name="examples"></a>Примеры  
 Это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] кода в test() функция выполняет следующие:  
  
- Создает новый объект путем вызова `Object` конструктор и присваивает указатель на новый объект для переменной Obj.  
  
- Создает новый элемент с именем элемента в объекте и присваивает этот элемент указатель на функцию cat.  
  
- Вызывает эту функцию. Так как он вызывается как метод, `this` указатель ссылается на объект Obj. Функция добавляет новый элемент, панели, чтобы объект.  
  
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
  
 Элементом управления, размещаемым на этом же веб-странице может получить указатель диспетчеризации для обработчиков сценариев из браузера. Элемент управления может быть учтены test() функции:  
  
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
  
 Код из элемента управления, тестирование и делает то же самое [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функция `test()`. Обратите внимание, что эти вызовы dispatch выполняются в выполняющийся [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ядра и изменить состояние обработчика:  
  
- Получает указатель диспетчеризации на cat функции с помощью `GetDispID()`.  
  
- Получает указатель диспетчеризации на объект функции с помощью `GetDispID()`.  
  
- Создает объект путем вызова объекта функции `InvokeEx()` и получает указатель диспетчеризации на вновь созданный объект.  
  
- Создает новый элемент, Elem, в объект с помощью `GetDispID()` с `fdexNameEnsure` флаг.  
  
- Помещает указатель диспетчеризации на cat в элементе в формате `InvokeEx()`.  
  
- Вызывает указатель диспетчеризации на cat как метод путем вызова `InvokeEx()` и передав указатель диспетчеризации на объект сконструированный как `this` указатель.  
  
- Метод cat создает новый элемент, в текущей строке `this` объекта.  
  
- Проверяет, что новый элемент, линейчатым диаграммам, созданный в сформированный объект с перечисление элементов, с помощью `GetNextDispID()`.  
  
  Код для элемента управления теста:  
  
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