---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
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
ms.openlocfilehash: 50f9f398b9193c776f8e2a823b78ce7b8da438b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153478"
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
 [in] Содержит текст выражения или операторы.  
  
 `nRadix`  
 [in] Основание системы счисления для использования.  
  
 `pstrDelimiter`  
 [in] Разделитель, конечный из скрипта блок. Когда `pstrCode` анализируется из потока текста узел обычно использует разделитель, например две одинарные кавычки («), чтобы обнаружить завершение блока скрипта. Этот параметр задает разделитель, используемый узлом, позволяя обработчик скриптов для предоставления некоторых условного примитивных предварительной обработки (например, замените одинарной кавычки ['] две одинарные кавычки для использования в качестве разделителя). Точный способ (и нужно ли) сценариев подсистемой, эта информация зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не используется разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 [in] Сочетание следующих флагов отладки текст:  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст представляет собой выражение, в отличие от инструкции. Этот флаг может влиять на анализе текста в некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение, он будет использоваться в вызывающем объекте.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не разрешать побочные эффекты. Если этот флаг установлен, вычисление выражения следует изменить ни одно состояние среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Позволяет точек останова во время оценки текста. Если этот флаг не установлен точки останова учитываются при вычислении текст.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Позволяет отчеты об ошибках во время оценки текста. Если этот флаг не установлен. затем ошибки не выводятся на узле во время вычисления.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Указывает, выражение будет вычисляться контекста кода, а не самого выражения|  
  
 `ppe`  
 [out] Возвращает выражение отладки для указанного текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает выражение отладки для указанного текста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)