---
title: MODULE_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32b0e89a69bc39e43d4ff4fbc4e8f4d5816565ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975391"
---
# <a name="moduleflags"></a>MODULE_FLAGS
Используется для описания модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_MODULE_FLAGS {   
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
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Участники  
 MODULE_FLAG_NONE  
 Указывает модуль не.  
  
 MODULE_FLAG_SYSTEM  
 Указывает системном модуле.  
  
 MODULE_FLAG_SYMBOLS  
 Задает модуль записи символов.  
  
 MODULE_FLAG_64BIT  
 Задает 64-разрядного модуля.  
  
 MODULE_FLAG_OPTIMIZED  
 Указывает, что модуль был оптимизирован. Это состояние отражается в **модули** окна.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Указывает, что модуль не был оптимизирован. Это состояние отражается в **модули** окна. Это состояние по умолчанию.  
  
## <a name="remarks"></a>Примечания  
 Используется для `m_dwModuleFlags` членом [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)