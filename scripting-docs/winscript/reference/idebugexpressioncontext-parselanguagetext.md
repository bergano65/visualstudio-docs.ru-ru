---
title: "IDebugExpressionContext::ParseLanguageText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Создает выражение отладки для указанного текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Содержит текст выражения или инструкции.  
  
 `nRadix`  
 [in] Основание системы счисления для использования.  
  
 `pstrDelimiter`  
 [in] Разделитель end из скрипта блока. Когда `pstrCode` анализируется из текстового потока, узел обычно использует разделители, такие как двух одинарных кавычки («), чтобы определить конец блока скрипта. Этот параметр определяет разделитель, который используется узел, позволяя обработчик скриптов для предоставления некоторых условного примитивов предварительной обработки (например, замените одинарная кавычка ['] две одинарные кавычки для использования в качестве разделителя). Как именно (и если) сценария подсистемой этих сведений зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не использовали разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 [in] Сочетание следующих флагов текста отладки:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст представляет собой выражение, в отличие от инструкции. Этот флаг может влиять на разборе текста в некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение, оно будет использоваться вызывающей стороной.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не разрешать побочные эффекты. Если этот флаг установлен, вычисление выражения должно измениться без состояния среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Позволяет точек останова во время оценки текста. Если этот флаг не установлен точки останова учитываются при вычислении текста.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Отчеты об ошибках позволяет во время оценки текста. Если этот флаг не установлен затем ошибки не отображаются в узле во время вычисления.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Указывает выражение, вычисляемое контекст кода, а не с самого выражения|  
  
 `ppe`  
 [out] Возвращает выражение отладки для указанного текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает выражений отладки для указанного текста.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)