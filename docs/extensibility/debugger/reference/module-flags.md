---
title: "MODULE_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_FLAGS
helpviewer_keywords: MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd55076df559b83c4bf4f3ed98fdea0e8bfd423a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="moduleflags"></a>MODULE_FLAGS
Используется для описания модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Члены  
 MODULE_FLAG_NONE  
 Указывает, ни один из модулей.  
  
 MODULE_FLAG_SYSTEM  
 Указывает системном модуле.  
  
 MODULE_FLAG_SYMBOLS  
 Указывает символ модуля.  
  
 MODULE_FLAG_64BIT  
 Задает 64-разрядного модуля.  
  
 MODULE_FLAG_OPTIMIZED  
 Указывает, что модуль был оптимизирован. Это состояние будет отражено в **модули** окна.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Указывает, что модуль не был оптимизирован. Это состояние будет отражено в **модули** окна. Это состояние по умолчанию.  
  
## <a name="remarks"></a>Примечания  
 Используется для `m_dwModuleFlags` членом [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)