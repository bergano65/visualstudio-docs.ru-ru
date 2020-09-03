---
title: REFERENCE_TYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 509c0bc4547ca057c39a6c07ba8ccbe63743b914
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204907"
---
# <a name="reference_type"></a>REFERENCE_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает ссылочный тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```csharp  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## <a name="members"></a>Участники  
 REF_TYPE_WEAK  
 Указывает слабую ссылку. Не может использоваться вместе с `REF_TYPE_STRONG` .  
  
 REF_TYPE_STRONG  
 Задает строгую ссылку. Не может использоваться вместе с `REF_TYPE_WEAK` .  
  
## <a name="remarks"></a>Remarks  
 Используется в качестве `dwRefType` члена структуры [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 Передается в качестве параметра в метод [сетреференцетипе](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
