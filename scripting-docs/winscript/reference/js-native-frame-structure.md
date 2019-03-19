---
title: Структура JS_NATIVE_FRAME | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a0777cf42b9ed9412602cb34ed2d521deca1fb9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150118"
---
# <a name="jsnativeframe-structure"></a>Структура JS_NATIVE_FRAME
Представляет кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Участники  
 `InstructionOffset`  
 Указатель инструкций.  
  
 `ReturnOffset`  
 Обратный адрес.  
  
 `FrameOffset`  
 Указатель кадра.  
  
 `StackOffset`  
 Указатель стека.  
  
## <a name="remarks"></a>Примечания  
 `JS_NATIVE_FRAME` Используется структура `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)