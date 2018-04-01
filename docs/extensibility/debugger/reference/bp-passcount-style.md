---
title: BP_PASSCOUNT_STYLE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e272c92bbcc7364c967fc37c1e57b915e6cb64ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Указывает условие, связанное с количеством проход точки останова, вызывающее срабатывание точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 BP_PASSCOUNT_NONE  
 Задает стиль счетчика проход не точки останова.  
  
 BP_PASSCOUNT_EQUAL  
 Задает стиль числа проход точки останова, равное. Точка останова срабатывает, если количество раз, когда точка останова будет достигнута равна числу проход.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Устанавливает стиль счетчика проход останова больше или равно. Точка останова срабатывает, если число попаданий точки останова равно или больше числа проход.  
  
 BP_PASSCOUNT_MOD  
 Указывает число проходов остаток от деления. Например, если этапа прошло типа `BP_PASSCOUNT_MOD` и передайте значение счетчика равно 4, точка останова срабатывает каждый раз, число попаданий кратно 4.  
  
## <a name="remarks"></a>Примечания  
 Используется для `stylePassCount` членом [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуру, которая в свою очередь является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)