---
title: JMC_CODE_SPEC | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2500a93ea928fbc1c472a60c9350136821a84ee4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040324"
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Эта структура используется для задания данных JustMyCode для модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Участники  
 fIsUserCode  
 Ненулевое значение (`TRUE`) Если модуль будет считаться пользовательского кода; в противном случае — нуль (`FALSE`) Если модуль должен обрабатываться как внешний код и не для отладки.  
  
 bstrModuleName  
 Имя модуля в вопросе.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается как список таких структур для [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) метод.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)