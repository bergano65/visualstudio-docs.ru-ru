---
title: Структура DebugStackFrameDescriptor | Документация Майкрософт
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
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955198"
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
  
## <a name="members"></a>Участники  
 `pdsf`  
 Объект кадра стека.  
  
 `dwMin`  
 Представление зависит от компьютера нижняя граница диапазона физических адресов, связанный с данным кадром стека.  
  
 `dwLim`  
 Представление зависит от компьютера верхнем диапазоне физических адресов, связанных с данным кадром стека.  
  
 `fFinal`  
 Флаг, указывающий, что кадр обрабатывается.  
  
 `punkFinal`  
 Если этот параметр не является `NULL`, следует остановить текущий перечислитель слияние, и новый должна быть запущена. Объект указывает, как для запуска нового перечисления.  
  
## <a name="remarks"></a>Примечания  
 Диспетчер отладки процессов использует эту структуру для сортировки кадры стека из нескольких обработчиков сценариев. По соглашению стеки растут вниз. Следовательно в архитектурах, где стеки растут вверх, адреса должны быть операции дополнения парами.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)