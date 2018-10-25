---
title: DOCCONTEXT_COMPARE | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f092666833b80dd59ed4b7b3345c379078ce2bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862961"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Указывает критерии для сравнения двух контекстов документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Участники  
 DOCCONTEXT_EQUAL  
 Найти первый контекст документа в списке, который равен целевой контекст документа.  
  
 DOCCONTEXT_LESS_THAN  
 Найти первый контекст документа в списке, который меньше, чем целевой контекст документа.  
  
 DOCCONTEXT_GREATER_THAN  
 Найти первый контекст документа в списке, который больше, чем целевой контекст документа.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Найти первый контекст документа в списке, который находится в том же документе целевой контекст документа.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [сравнения](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) метод.  
  
 Эти значения используются для указания критерии сравнения для нахождения первого контекст документа в виде списка. Контекст документа предоставляется список контекстов документа сравнивать себя с помощью `IDebugDocumentContext2::Compare` метод. Первый контекст документа в списке, для которого является оператор сравнения `true` затем возвращается.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)