---
title: Иактивескриптпарсепроцедуре::P Арсепроцедуретекст | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53ed29c3e283af0f923590851cf9bf0655f7ac08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561535"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Анализирует данную процедуру кода и добавляет процедуру в пространство имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 окне Адрес текста процедуры для вычисления. Интерпретация этой строки зависит от языка сценариев.  
  
 `pstrFormalParams`  
 окне Адрес формальных имен параметров для процедуры. Имена параметров должны быть разделены соответствующими разделителями для обработчика скриптов. Имена не должны заключаться в круглые скобки.  
  
 `pstrProcedureName`  
 окне Адрес имени процедуры для синтаксического анализа.  
  
 `pstrItemName`  
 окне Адрес имени элемента, предоставляющего контекст, в котором должна быть вычислена процедура. Если этот параметр имеет значение `NULL`, код вычисляется в глобальном контексте обработчика скриптов.  
  
 `punkContext`  
 окне Адрес объекта контекста. Этот объект зарезервирован для использования в среде отладки, где такой контекст может быть предоставлен отладчиком для представления активного контекста времени выполнения. Если этот параметр имеет значение `NULL`, подсистема использует `pstrItemName` для задания контекста.  
  
 `pstrDelimiter`  
 окне Адрес разделителя в конце процедуры. Когда `pstrCode` анализируется из потока текста, узел обычно использует разделитель, например две одинарные кавычки (' '), для обнаружения конца процедуры. Этот параметр задает разделитель, используемый узлом, позволяя обработчику скриптов предоставить некоторую условную предварительную обработку примитивов (например, заменить одинарную кавычку ['] двумя одинарными кавычками для использования в качестве разделителя). Точно то, как (и если) обработчик сценариев использует эти сведения, зависит от обработчика скриптов. Задайте для этого параметра значение `NULL`, если узел не использовал разделитель для обозначения конца процедуры.  
  
 `dwSourceContextCookie`  
 окне Определяемое приложением значение, используемое в целях отладки.  
  
 `ulStartingLineNumber`  
 окне Отсчитываемое от нуля значение, которое указывает строку, с которой начнется анализ.  
  
 `dwFlags`  
 окне Флаги, связанные с процедурой. Может быть сочетанием следующих значений:  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Указывает, что код в `pstrCode` является выражением, представляющим возвращаемое значение процедуры. По умолчанию код может содержать выражение, список операторов или любые другие возможности, которые можно использовать в процедуре с помощью языка сценариев.|  
|SCRIPTPROC_IMPLICIT_THIS|Указывает, что указатель `this` включен в область действия процедуры.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Указывает, что родительские элементы указателя `this` включены в область действия процедуры.|  
  
 `ppdisp`  
 заполняет Адрес указателя для объекта, содержащего глобальные методы и свойства скрипта. Если обработчик скриптов не поддерживает такой объект, возвращается `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_NOTIMPL`|Этот метод не поддерживается. Обработчик скриптов не поддерживает добавление процедур в пространство имен во время выполнения.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов находится в неинициализированном или закрытом состоянии).|  
|`OLESCRIPT_E_SYNTAX`|В процедуре произошла неопределенная синтаксическая ошибка.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчеризации; параметр `ppdisp` имеет значение `NULL`.|  
  
## <a name="remarks"></a>Заметки  
 Во время этого вызова не вычисляется код скрипта; Вместо этого процедура компилируется в состояние скрипта, где скрипт может быть вызван позже.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)