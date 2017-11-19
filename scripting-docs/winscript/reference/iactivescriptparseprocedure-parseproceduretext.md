---
title: "IActiveScriptParseProcedure::ParseProcedureText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Выполняет синтаксический анализ кода данной процедуры и добавляет процедуру в пространство имен.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 [in] Адрес текст процедуры для оценки. Интерпретация этой строки зависит от языка скриптов.  
  
 `pstrFormalParams`  
 [in] Адрес имена формальных параметров для процедуры. Имена параметров должны быть разделены соответствующие разделителей для обработчика сценариев. Имена не должны заключаться в круглые скобки.  
  
 `pstrProcedureName`  
 [in] Адрес имени процедуры для синтаксического анализа.  
  
 `pstrItemName`  
 [in] Адрес, предоставляющий контекст, в котором процедура вычисляемое имя элемента. Если этот параметр равен `NULL`, вычисления кода в глобальном контексте обработчика скриптов.  
  
 `punkContext`  
 [in] Адрес контекста объекта. Этот объект зарезервирован для использования в отладочной среде, где может быть указано контексте отладчиком для представления активный контекст во время выполнения. Если этот параметр имеет `NULL`, используемый подсистемой `pstrItemName` для определения контекста.  
  
 `pstrDelimiter`  
 [in] Адрес разделитель end из процедуры. Когда `pstrCode` анализируется из текстового потока, узел обычно использует разделители, такие как двумя одинарными кавычками («), чтобы обнаружить завершение процедуры. Этот параметр определяет разделитель, который используется узел, позволяя обработчик скриптов для предоставления некоторых условного примитивов предварительной обработки (например, замените одинарная кавычка ['] две одинарные кавычки для использования в качестве разделителя). Как именно (и если) сценария делает ядра, использование этих сведений зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не использовался разделитель, чтобы отметить конец процедуры.  
  
 `dwSourceContextCookie`  
 [in] Определяемые приложением значения, который используется в целях отладки.  
  
 `ulStartingLineNumber`  
 [in] Отсчитываемый от нуля значение, которое указывает строку, с которой начинается синтаксический анализ с.  
  
 `dwFlags`  
 [in] Флаги, связанные с процедурой. Может представлять собой сочетание этих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Указывает, что код в `pstrCode` выражение, которое представляет возвращаемое значение процедуры. По умолчанию код может содержать выражения, список инструкций или любые объекты, в противном случае допустимые в процедуре язык скрипта.|  
|SCRIPTPROC_IMPLICIT_THIS|Указывает, что `this` указатель мыши входит в область процедуры.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Указывает, что родительские объекты `this` указатель входят в область процедуры.|  
  
 `ppdisp`  
 [out] Адрес указателя на объект, содержащий глобальные методы и свойства сценария в файле. Если обработчик скриптов не поддерживает такой объект `NULL` возвращается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_NOTIMPL`|Этот метод не поддерживается. Обработчик скриптов не поддерживает добавление во время выполнения процедуры пространства имен.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик скриптов находится в состоянии неактивное состояние или закрытые).|  
|`OLESCRIPT_E_SYNTAX`|Неизвестная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объекта распределения; `ppdisp` параметра равным `NULL`.|  
  
## <a name="remarks"></a>Примечания  
 Код скрипта не вычисляется во время данного вызова; Вместо этого процедура компилируется в состояние сценарий, где может вызываться с помощью скрипта позже.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)