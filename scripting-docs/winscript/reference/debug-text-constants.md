---
title: "Константы DEBUG_TEXT | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugtext-constants"></a>Константы DEBUG_TEXT
Во время [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст представляет собой выражение, в отличие от инструкции. Этот флаг может влиять на разборе текста в некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение, оно будет использоваться вызывающей стороной.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не разрешать побочные эффекты. Если этот флаг установлен, вычисление выражения должно измениться без состояния среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Разрешить точки останова во время оценки текста. Если этот флаг не установлен, точки останова будет игнорироваться во время оценки текста.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Разрешить отчеты об ошибках во время оценки текста. Если этот флаг не установлен, затем ошибки не возникнет узлу во время вычисления.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Показывает, что выражение вычисляется в контексте кода, а не с самого выражения.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)