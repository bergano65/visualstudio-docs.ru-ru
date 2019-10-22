---
title: Структура Дебугстаккфрамедескриптор | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576552"
---
# <a name="debugstackframedescriptor-structure"></a>Структура DebugStackFrameDescriptor
Перечисляет кадры стека и объединяет результаты нескольких перечислителей в одном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 Зависящее от компьютера представление нижнего диапазона физических адресов, связанных с этим кадром стека.  
  
 `dwLim`  
 Зависящее от компьютера представление верхнего диапазона физических адресов, связанных с этим кадром стека.  
  
 `fFinal`  
 Флаг, указывающий, что кадр обрабатывается.  
  
 `punkFinal`  
 Если этот параметр не `NULL`, слияние текущего перечислителя должно останавливаться, и должно быть запущено новое. Объект указывает, как запустить новое перечисление.  
  
## <a name="remarks"></a>Заметки  
 Диспетчер отладки процессов использует эту структуру для сортировки кадров стека из нескольких обработчиков сценариев. По соглашению стеки увеличиваются. Следовательно, в архитектурах, где увеличиваются стеки, адреса должны быть парных.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)