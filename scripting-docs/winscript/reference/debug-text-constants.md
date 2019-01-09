---
title: Константы DEBUG_TEXT | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64cd178dc997f30f7afbf80279dda42d3c1b7be4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089353"
---
# <a name="debugtext-constants"></a>Константы DEBUG_TEXT
Используется во время [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст представляет собой выражение, в отличие от инструкции. Этот флаг может влиять на анализе текста в некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение, он будет использоваться в вызывающем объекте.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не разрешать побочные эффекты. Если этот флаг установлен, вычисление выражения следует изменить ни одно состояние среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Разрешить точки останова во время оценки текста. Если этот флаг не установлен, точки останова будет игнорироваться во время оценки текста.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Разрешить отчеты об ошибках во время оценки текста. Если этот флаг не установлен, то ошибки не возникнет на узле во время вычисления.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Указывает, что выражение будет вычисляться контекста кода, а не само выражение.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)