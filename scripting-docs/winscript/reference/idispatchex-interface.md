---
title: "Интерфейс IDispatchEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx — интерфейс"
  - "IDispatchEx — интерфейс, об интерфейсе IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Интерфейс IDispatchEx
`IDispatchEx`, является расширением интерфейса `IDispatch`, поддерживает функции подходят для динамических языков, как скриптовые языки.  Этот раздел описывает интерфейс самого `IDispatchEx`, различия между `IDispatch` и `IDispatchEx` и обоснование для расширений.  Ожидается, что читатели знакомы с `IDispatch` и имеют доступ к документации по `IDispatch`.  
  
## Заметки  
 `IDispatch` было инициировано существенным для Microsoft Visual Basic.  Основное ограничение `IDispatch`, что он подразумевается, что объекты является статическим.  Иначе говоря, поскольку объекты не изменялись во время выполнения сведения о типе может полностью описать их во время компиляции.  Динамические модели времени выполнения, находитьы в языках скриптов, как visual basic scripting edition \(VBScript\) и [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и объектные модели динамического HTML как требуют более гибкого интерфейса.  
  
 `IDispatchEx` было инициировано, чтобы все службы `IDispatch`, а также несколько расширений, которые подходят для динамических языков, как поздно\- привязанных скриптовые языки.  Дополнительные функции `IDispatchEx` за этими указанными `IDispatch`:  
  
-   Добавление новых членов к объекту \("expando"\) — применяется `GetDispID` с флагом `fdexNameEnsure`.  
  
-   Удаление членов объект\- использования `DeleteMemberByName` или `DeleteMemberByDispID`.  
  
-   С учетом регистра операция\- использование `fdexNameCaseSensitive` или `fdexNameCaseInsensitive` диспетчера.  
  
-   Поиск элемента с использованием `fdexNameImplicit` неявной имя\-.  
  
-   Список идентификаторов dispid объект\- использования `GetNextDispID`.  
  
-   Сопоставление DISPID в имя\- использовании `GetMemberName` элемента.  
  
-   Получение свойств участник\- использования `GetMemberProperties` объекта.  
  
-   Вызов метода с указатель\- использованием `InvokeEx``this` с DISPATCH\_METHOD.  
  
-   Разрешить обозреватели, которые поддерживают понятие пробелов имени, чтобы получить родительский пространства имен объект\- использования `GetNameSpaceParent`.  
  
 Объекты, поддерживающие `IDispatchEx` также могут поддерживать `IDispatch` для обратной совместимости.  Динамическая характера объектов, поддерживающих `IDispatchEx` имеет несколько прикосновенностей для интерфейса `IDispatch` этих объектов.  Например, `IDispatch` предположение выполняет следующее:  
  
-   Элемент и идентификаторов dispid, должны оставаться постоянным параметр в течение времени существования объекта.  Это позволяет клиенту получение идентификаторов dispid один раз и кэширование их в кэш для дальнейшего использования.  
  
 Поскольку `IDispatchEx` допускает добавление и удаление членов, набор допустимых идентификаторов dispid не остается постоянной.  Однако `IDispatchEx` требует сопоставление между DISPID и именем остается постоянной.  Это значит, что если элемент удален.  
  
-   Идентификатор DISPID нельзя использовать повторно, пока не создает элемент с таким же именем.  
  
-   Идентификатор DISPID должно оставаться допустимыми для `GetNextDispID`.  
  
-   Идентификатор DISPID должно быть принятьо надлежащим образом любым `IDispatch` или `IDispatchEx` метод\- они должны определить член как удалятьо и вернуть соответствующий код ошибки \(как правило, DISP\_E\_MEMBERNOTFOUND или S\_FALSE\).  
  
## Примеры  
 Этот код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в функциональном тесте \(\) выполняет следующие действия:  
  
-   Создает новый объект путем вызова конструктора `Object` и присвоит указатель на новый объект переменной Obj.  
  
-   Создает новый элемент с именем Elem в объекте и присвоить этому элементу указатель на коту функции.  
  
-   Вызывает данную функцию.  Поскольку она вызывается как метод, указатель `this` ссылается на объект Obj.  Функция добавить новый элемент, черта, к объекту.  
  
 Полный код HTML:  
  
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
  
 Помещенный элемент управления на этой странице можно получить указатель диспетчеризации к обработчикам скрипта из браузера.  Элемент управления может затем ссылаться тест func \(\):  
  
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
  
 Закодируйте от элемента управления теста выполните то же самое, что и функция `test()`[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Обратите внимание, что эти диспетчера позвонены в запущенный обработчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и изменение состояния подсистемы:  
  
-   Получает указатель на функцию, с помощью диспетчера кота `GetDispID()`.  
  
-   Получает указатель на функцию объекта с помощью диспетчера `GetDispID()`.  
  
-   Создает объект путем вызова функции с `InvokeEx()` объекта и возвращает указатель диспетчеризации на вновь созданный объект.  
  
-   Создает новый элемент Elem, в объекте с помощью `GetDispID()` с флагом `fdexNameEnsure`.  
  
-   Указатель на коту в элемент с помощью диспетчера `InvokeEx()`.  
  
-   Вызывает указатель диспетчера к коту как метод путем вызова `InvokeEx()` и передачи указатель на созданный объект диспетчера как указатель `this`.  
  
-   Метод кота создает новый элемент, черта в текущем объекте `this`.  
  
-   Проверяет, что новый элемент, черта, построенных был создан в объекте, выполняя перечисление по элементам с помощью `GetNextDispID()`.  
  
 Код для элемента управления теста.  
  
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
  
## Методы  
 [Методы IDispatchEx](../../winscript/reference/idispatchex-methods.md)