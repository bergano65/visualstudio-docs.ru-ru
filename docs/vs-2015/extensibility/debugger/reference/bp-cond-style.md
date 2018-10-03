---
title: BP_COND_STYLE | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5e0df33ef462d6b1b8bbe013f30baab894ea82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559551"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [BP_COND_STYLE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-cond-style).  
  
Указывает стиль условие точки останова для ожидающих и привязан точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Точка останова срабатывает в том случае, когда достигается положение точки останова. Не указано условие точки останова.  
  
 BP_COND_WHEN_TRUE  
 Срабатывает точка останова, только если условное выражение, связанные с точкой останова принимает значение `true`.  
  
 BP_COND_WHEN_CHANGED  
 Срабатывает точка останова только в том случае, если значение условного выражения, связанное с точкой останова отличается от его предыдущей оценки.  
  
## <a name="remarks"></a>Примечания  
 Используется для `styleCondition` членом [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

