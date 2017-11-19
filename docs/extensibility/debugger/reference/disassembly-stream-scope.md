---
title: "DISASSEMBLY_STREAM_SCOPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords: DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cbd0ea73c7efea5cee570548dec5570ffc53b42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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