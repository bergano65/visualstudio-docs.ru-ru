---
title: PROGRAM_DESTROY_FLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1c32ef0e56871cb2db48d769c9d4c82c9aad076
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294246"
---
# <a name="programdestroyflags"></a>PROGRAM_DESTROY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет допустимые значения в программе уничтожить флаги.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```csharp  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## <a name="terms"></a>Термины  
 PROGRAM_DESTROY_CONTINUE_DEBUGGING  
 Уничтожить программы, но продолжить отладку.  
  
## <a name="remarks"></a>Примечания  
 Возвращает перечисление [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)

