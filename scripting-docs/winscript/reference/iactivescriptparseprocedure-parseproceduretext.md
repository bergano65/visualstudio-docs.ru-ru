---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
Анализирует заданную процедура кода и добавляет процедуры в пространстве имен.  
  
## Синтаксис  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### Параметры  
 `pstrCode`  
 \[in\] адрес текст процедуры, которые необходимо вычислить.  Интерпретация зависит от этой строки язык сценариев.  
  
 `pstrFormalParams`  
 \[in\] адрес имен формальных параметров для процедуры.  Имена параметров необходимо отделить с соответствующими разделителями для обработчика скриптов.  Имена не должны быть заключены в скобки.  
  
 `pstrProcedureName`  
 \[in\] адрес имя процедуры, которое необходимо проанализировать.  
  
 `pstrItemName`  
 \[in\] адрес имя элемента, которое предоставляет контекст, в котором необходимо оценить процедуры.  Если этот параметр `NULL`, код выполняется в контексте обработчика скриптов глобальном.  
  
 `punkContext`  
 \[in\] адрес объекта контекста.  Этот объект зарезервирован для использования в среду отладки, где тот контекст может быть предусмотрен отладчиком, представленный активный контекст среды выполнения.  Если этот параметр `NULL`, система использует `pstrItemName` для указания контекста.  
  
 `pstrDelimiter`  
 \[in\] адрес разделителя элемент \-\- процедуры.  При `pstrCode` анализироватьо из потока текста, основное приложение обычно использует разделитель, например 2 одинарных кавычки \("\), чтобы определить окончание процедуры.  Этот параметр задает разделитель, используемый основным приложением, что обработчик скриптов, чтобы обеспечить какую\-либо условную предобработку примитивов \(например, заменящ одинарная кавычка \('\) с 2 одинарными кавычками для использования в качестве разделителя\).  То, как \(и, если\), то обработчик скриптов использует этот зависит от информации обработчика скриптов.  Установите этот параметр в `NULL` если основное приложение не использует разделитель для обозначения конца процедуры.  
  
 `dwSourceContextCookie`  
 \[in\] Приложение\- указанное значение, которое используется для отладки.  
  
 `ulStartingLineNumber`  
 \[in\] Нул\- значение, указывающее на основе которой начинается на линии синтаксического анализа.  
  
 `dwFlags`  
 \[in\] флаги, связанные с процедурой.  Может оказаться сочетание этих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTPROC\_ISEXPRESSION|Указывает, что выполнение кода в `pstrCode` выражение, которое представляет возвращаемое значение процедуры.  По умолчанию код может содержать выражения, список выписок или что\-нибудь еще разрешенные в процедуре языком скрипта.|  
|SCRIPTPROC\_IMPLICIT\_THIS|Указывает, что указатель `this` включен в области процедуры.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|Указывает, что указатель `this` родительские объекты включаются в области процедуры.|  
  
 `ppdisp`  
 \[out\] адрес указателя для объекта, содержащего методы и свойства сценария глобальные.  Если обработчик скриптов не поддерживает такой объект, `NULL` возвращается.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_NOTIMPL`|Этот метод не поддерживается.  Обработчик скриптов не поддерживает добавление времени выполнения процедур в пространстве имен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов в неинициализированном состоянии или закрыть\).|  
|`OLESCRIPT_E_SYNTAX`|Произошла неопознанная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчера; параметр `ppdisp` ему присваивается `NULL`.|  
  
## Заметки  
 Код скрипта не оценивается во время этого вызова; вместо этого процедуру компилироватьа в состояние сценария, где она может быть Позвонитьа скриптом в будущем.  
  
## См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)