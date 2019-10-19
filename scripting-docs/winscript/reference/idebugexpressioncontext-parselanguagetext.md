---
title: IDebugExpressionContext::P Арселангуажетекст | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573154"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Создает выражение отладки для указанного текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 окне Содержит текст выражения или операторов.  
  
 `nRadix`  
 окне Используемое основание системы счисления.  
  
 `pstrDelimiter`  
 окне Разделитель-блок конца скрипта. Когда `pstrCode` анализируется из потока текста, узел обычно использует разделитель, например две одинарные кавычки (' '), для обнаружения конца блока скрипта. Этот параметр задает разделитель, используемый узлом, позволяя обработчику скриптов предоставить некоторую условную предварительную обработку примитивов (например, заменить одинарную кавычку ['] двумя одинарными кавычками для использования в качестве разделителя). Точно то, как (и если) обработчик скриптов использует эти сведения, зависит от обработчика скриптов. Задайте для этого параметра значение `NULL`, если узел не использовал разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 окне Сочетание следующих флагов текста отладки:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст является выражением, а не оператором. Этот флаг может повлиять на способ анализа текста на некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение доступно, вызывающий объект будет использовать его.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не допускайте побочных эффектов. Если этот флаг установлен, вычисление выражения не должно изменять состояние среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Разрешает точки останова во время вычисления текста. Если этот флаг не установлен, точки останова игнорируются во время вычисления текста.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Разрешает отчеты об ошибках во время вычисления текста. Если этот флаг не установлен, в процессе оценки ошибки не передаются на узел.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Указывает, что выражение должно быть вычислено в контекст кода вместо того, чтобы выполнять само выражение|  
  
 `ppe`  
 заполняет Возвращает выражение отладки для указанного текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод создает выражение отладки для указанного текста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)