---
title: Перечисление ЕРРОРРЕСУМЕАКТИОН | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575865"
---
# <a name="errorresumeaction-enumeration"></a>Перечисление ERRORRESUMEACTION
Описывает, как будет происходить продолжение выполнения после ошибки времени выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Повторно выполняет инструкцию, вызвавшую ошибку.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Позволяет обработчику языка выполнить обработку ошибки.|  
|ERRORRESUMEACTION_SkipErrorStatement|Возобновляет выполнение в коде после оператора, вызвавшего ошибку.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)