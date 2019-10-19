---
title: Константы DEBUG_TEXT | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577370"
---
# <a name="debug_text-constants"></a>Константы DEBUG_TEXT
Используется во время [IDebugExpressionContext::P арселангуажетекст](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Указывает, что текст является выражением, а не оператором. Этот флаг может повлиять на способ анализа текста на некоторых языках.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Если возвращаемое значение доступно, вызывающий объект будет использовать его.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Не допускайте побочных эффектов. Если этот флаг установлен, вычисление выражения не должно изменять состояние среды выполнения.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Разрешение точек останова во время вычисления текста. Если этот флаг не установлен, точки останова будут игнорироваться во время вычисления текста.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Разрешить отчеты об ошибках во время вычисления текста. Если этот флаг не установлен, то во время оценки ошибки не будут переданы на узел.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Указывает, что выражение должно быть вычислено в контекст кода вместо того, чтобы выполнять само выражение.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)