---
title: "Структура DebugStackFrameDescriptor | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>Структура DebugStackFrameDescriptor
Перечисляет кадры стека и объединяет результаты нескольких перечислителей в одном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Члены  
 `pdsf`  
 Объект кадра стека.  
  
 `dwMin`  
 Представление зависит от компьютера с нижним диапазоном физических адресов, связанный с данным кадром стека.  
  
 `dwLim`  
 Представление зависит от компьютера верхнего диапазона физических адресов, связанных с данным кадром стека.  
  
 `fFinal`  
 Флаг, указывающий, выполняется кадр.  
  
 `punkFinal`  
 Если этот параметр не является `NULL`, следует остановить текущее слияние перечислителя и новый должна быть запущена. Объект указывает, как запустить новое перечисление.  
  
## <a name="remarks"></a>Примечания  
 Чтобы отсортировать кадры стека из нескольких обработчиков сценариев в диспетчер отладки процессов использует следующую структуру. По соглашению стеки растут вниз. Следовательно для архитектур, где стеки растут вверх, адреса должны поддерживать операции дополнения парных.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)