---
title: DISASSEMBLY_STREAM_SCOPE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0c72d0f14da9840c0a77d5ae88cb0acb5b54cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102071"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Указывает область потока Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 DSS_HUGE  
 Указывает, что декомпозицию контекст кода будет создавать дополнительные выходные данные, чем клиент обычно требуется получить в рамках одного вызова.  
  
 DSS_FUNCTION  
 Указывает, что поддается функции, содержащиеся в контекст кода. Указывает, что поток Дизассемблированный код представляет функции, при возврате [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.  
  
 DSS_MODULE  
 При возврате `IDebugDisassemblyStream2::GetScope` метода, указывает, что поток Дизассемблированный код представляет модуль.  
  
 DSS_ALL  
 Указывает Дизассемблированный код для всему адресному пространству.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод и возвращенный [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.  
  
 Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)