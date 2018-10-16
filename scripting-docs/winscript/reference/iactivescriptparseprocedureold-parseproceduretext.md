---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Документы Microsoft
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
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725004"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Выполняет синтаксический анализ кода данной процедуры и добавляет процедуру анонимные пространства имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Имена формальных параметров для процедуры. Имена параметров должны быть разделены соответствующие разделителей для обработчика сценариев. Имена не должны заключаться в круглые скобки.  
  
 `pstrItemName`  
 [in] Имя именованного элемента, который предоставляет контекст, в котором необходимо оценить процедуры. Если этот параметр равен `NULL`, вычисления кода в глобальном контексте обработчика скриптов.  
  
 `punkContext`  
 [in] Объект контекста. Этот объект зарезервирован для использования в отладочной среде, где может быть указано контексте отладчиком для представления активный контекст во время выполнения. Если этот параметр имеет `NULL`, используемый подсистемой `pstrItemName` для определения контекста.  
  
 `pstrDelimiter`  
 [in] Разделитель end из процедуры. Когда `pstrCode` анализируется из текстового потока, узел обычно использует разделители, такие как двумя одинарными кавычками («), чтобы обнаружить завершение процедуры. Этот параметр определяет разделитель, который используется узел, позволяя обработчик скриптов для предоставления некоторых условное примитивов предварительной обработки (например, замените одинарные кавычки для использования в качестве разделителя одинарная кавычка [']). Как именно (и если) сценария подсистемой этих сведений зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не использовался разделитель, чтобы отметить конец процедуры.  
  
 `dwSourceContextCookie`  
 [in] Определяемые приложением значения, который используется в целях отладки.  
  
 `ulStartingLineNumber`  
 [in] Отсчитываемый от нуля значение, которое указывает на строку, с которой начинается синтаксический анализ.  
  
 `dwFlags`  
 [in] Флаги, связанные с процедурой. Может быть сочетанием этих значений.  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Указывает, что код в `pstrCode` выражение, которое представляет возвращаемое значение процедуры.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Указывает, что `this` указатель мыши входит в область процедуры.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Указывает, что родительские объекты `this` указатель входят в область процедуры.|  
  
 `ppdisp`  
 [out] Возвращает оболочку диспетчеризации, где метод по умолчанию — процедуры синтаксического анализа с помощью данного метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_NOTIMPL`|Этот метод не поддерживается. Обработчик скриптов не поддерживает добавление во время выполнения процедуры пространства имен.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик скриптов находится в состоянии неактивное состояние или закрытые).|  
|`OLESCRIPT_E_SYNTAX`|Неизвестная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объекта распределения; `ppdisp`параметра равным `NULL`.|  
  
## <a name="remarks"></a>Примечания  
 Код скрипта не вычисляется во время данного вызова; скорее, что процедура компилируется в метод на `ppdisp` где может вызываться с помощью скрипта позже.  
  
 Этот интерфейс является устаревшим для `IActiveScriptParseProcedure` интерфейса. `IActiveScriptParseProcedure::ParseProcedureText` Метод похож на этот метод, но разрешается указывать имя процедуры. Во всех случаях `IActiveScriptParseProcedure::ParseProcedureText` следует использовать.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)