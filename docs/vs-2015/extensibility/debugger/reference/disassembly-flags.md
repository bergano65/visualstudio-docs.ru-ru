---
title: DISASSEMBLY_FLAGS | Документация Майкрософт
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
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85c5e4a5b0cc5dbdcff5750ce5c87d170bb9bd20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561946"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DISASSEMBLY_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/disassembly-flags).  
  
Задает флаги для Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Участники  
 DF_DOCUMENTCHANGE  
 Указывает, что эта инструкция находится в другой документ, отличный от предыдущего.  
  
 DF_DISABLED  
 Указывает, что эта инструкция будет выполнена.  
  
 DF_INSTRUCTION_ACTIVE  
 Указывает, что эта инструкция является одним из далее инструкциям для выполнения (может быть несколько).  
  
 DF_DATA  
 Указывает, что эта инструкция действительно данных (не в коде).  
  
 DF_HASSOURCE  
 Указывает, что эта инструкция имеет источник. Некоторые инструкции, такие как коллекции кода профилирования или сборки мусора, имеют нет соответствующего источника.  
  
 DF_DOCUMENT_CHECKSUM  
 Указывает, что `bstrDocumentUrl` поле содержит данные контрольной суммы после URL-адрес документа. См. в разделе "Примечания" [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуру как хранятся данные контрольной суммы.  
  
## <a name="remarks"></a>Примечания  
 Используется в качестве `dwFlags` членом [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

