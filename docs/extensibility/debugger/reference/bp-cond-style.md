---
title: BP_COND_STYLE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b3d7bd22633985973975cb54d54ab3eb0837e30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Задает стиль условие точки останова для ожидающих и привязку точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Участники  
 BP_COND_NONE  
 Срабатывает точка останова при достижении положение точки останова. Не указано условие точки останова.  
  
 BP_COND_WHEN_TRUE  
 Точка останова срабатывает, только если условное выражение, связанные с точкой останова равно `true`.  
  
 BP_COND_WHEN_CHANGED  
 Срабатывает точка останова только в том случае, если значение условного выражения, связанной с точкой останова отличается от его предыдущей оценки.  
  
## <a name="remarks"></a>Примечания  
 Используется для `styleCondition` членом [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)