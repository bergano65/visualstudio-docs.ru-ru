---
title: DISASSEMBLY_STREAM_SCOPE | Документация Майкрософт
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
ms.openlocfilehash: 860d563abd5922ecf0461ed5f03ffa231ba9450f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831163"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Задает область потока Дизассемблированный код.  
  
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
 Указывает, что Дизассемблирование контекст кода будет создавать дополнительные выходные данные, чем клиент обычно необходимо получить в одном вызове.  
  
 DSS_FUNCTION  
 Указывает, что функции, содержащиеся в контексте кода должны быть дизассемблирован. Указывает, что поток Дизассемблированный код представляет функцию, при возврате [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.  
  
 DSS_MODULE  
 При возврате `IDebugDisassemblyStream2::GetScope` методом, указывает, что поток Дизассемблированный код представляет модуль.  
  
 DSS_ALL  
 Указывает Дизассемблированный код для во всем адресном пространстве.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод и возвращенный [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.  
  
 Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)