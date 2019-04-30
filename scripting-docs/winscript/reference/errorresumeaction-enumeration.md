---
title: Перечисление ERRORRESUMEACTION | Документация Майкрософт
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
ms.openlocfilehash: d92b4b2e00b25a509d29511008876d781c8a577a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955183"
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
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Повторно выполняет инструкцию, породившее ошибку.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Позволяет обработать ошибку модуль языка.|  
|ERRORRESUMEACTION_SkipErrorStatement|Возобновляет выполнение в коде после оператора, породившее ошибку.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)