---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec100214a43be6e1faf5e229ce6452432065002b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093396"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Выполняет синтаксический анализ данного кода процедуры и добавляет процедуру анонимные пространства имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 [in] Текст процедуры для оценки. Интерпретация этой строки зависит от языка скриптов.  
  
 `pstrFormalParams`  
 [in] Имена формальных параметров для процедуры. Имена параметров должны быть разделены с помощью соответствующих разделителей для обработчика скриптов. Имена не должны заключаться в круглые скобки.  
  
 `pstrItemName`  
 [in] Имя именованного элемента, который предоставляет контекст, в котором будет вычисляться процедуры. Если этот параметр равен `NULL`, то код вычисляется в глобальном контексте обработчика скриптов.  
  
 `punkContext`  
 [in] Объект контекста. Этот объект зарезервирован для использования в среде отладки, где такой контекст может быть предоставлен отладчиком для представления активный контекст среды выполнения. Если этот параметр имеет `NULL`, модуль использует `pstrItemName` для определения контекста.  
  
 `pstrDelimiter`  
 [in] Разделитель end из процедуры. Когда `pstrCode` анализируется из потока текста узел обычно использует разделитель, например две одинарные кавычки («), чтобы обнаружить завершение процедуры. Этот параметр задает разделитель, используемый узлом, позволяя обработчик скриптов для предоставления некоторых условных операций, примитивные предварительной обработки (например, заменив две одинарные кавычки для использования в качестве разделителя знак одинарной кавычки [']). Точный способ (и нужно ли) сценариев подсистемой, эта информация зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не используется разделитель для обозначения конца процедуры.  
  
 `dwSourceContextCookie`  
 [in] Определяемый приложением значение, используемое для отладки.  
  
 `ulStartingLineNumber`  
 [in] Отсчитываемый от нуля значение, указывающее, какой строки начинается синтаксический анализ.  
  
 `dwFlags`  
 [in] Флаги, связанные с процедурой. Может представлять собой сочетание этих значений.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Указывает, что код в `pstrCode` выражение, которое представляет возвращаемое значение процедуры.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Указывает, что `this` указатель входит в область процедуры.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Указывает, что родителям `this` указатель, включаются в область процедуры.|  
  
 `ppdisp`  
 [out] Возвращает оболочку диспетчеризации, где метод по умолчанию является процедурой, синтаксический анализ с помощью данного метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_NOTIMPL`|Этот метод не поддерживается. Обработчик скриптов не поддерживает добавление во время выполнения процедуры в пространстве имен.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов находится в неинициализированном или закрытом состоянии).|  
|`OLESCRIPT_E_SYNTAX`|Произошла Неуказанная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчеризации; `ppdisp`параметр имеет значение `NULL`.|  
  
## <a name="remarks"></a>Примечания  
 Код скрипта не вычисляется во время этого вызова; Вместо этого процедура компилируется в метод по `ppdisp` где может быть вызвана сценарий позже.  
  
 Этот интерфейс устарел, вместо него используется `IActiveScriptParseProcedure` интерфейс. `IActiveScriptParseProcedure::ParseProcedureText` Метод аналогичен методу этот метод, но он позволяет указывать имя процедуры. В любом случае `IActiveScriptParseProcedure::ParseProcedureText` следует использовать.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)