---
title: Перечисление ERRORRESUMEACTION | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640614"
---
# <a name="errorresumeaction-enumeration"></a>Перечисление ERRORRESUMEACTION
Описывает, как будет происходить продолжение выполнения после ошибки времени выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Повторно выполняет инструкцию, которое вызвало ошибку.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Позволяет обработать ошибку обработчик языка.|  
|ERRORRESUMEACTION_SkipErrorStatement|Возобновляет выполнение в коде после оператора, которое вызвало ошибку.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)