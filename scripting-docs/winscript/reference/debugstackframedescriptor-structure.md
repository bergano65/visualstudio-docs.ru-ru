---
title: Структура DebugStackFrameDescriptor | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c50c717cad626f4caf634c6a83b2af7213b78f83
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088482"
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