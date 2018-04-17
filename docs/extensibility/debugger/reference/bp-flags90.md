---
title: BP_FLAGS90 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f8153f3fb2419e26f7e7d3a741ae4c79c9272a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bpflags90"></a>BP_FLAGS90
Перечисляет допустимые значения для необязательные флаги. Необязательные флаги могут использоваться для указания дополнительных сведений, если установить точку останова. Это перечисление расширяет [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 BP90_FLAG_NONE  
 Задает флаг без точки останова.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Указывает, что модуль отладки (DE) следует сопоставить точки останова с помощью позицию в документе. Это значение применимо только к точки останова в скрипт ориентированного исходных файлов как Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Указывает, что точка останова должны обрабатываться с помощью модуля отладки, но, модуль отладки в конечном счете должны не останавливаться; то есть [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не следует отправлять объект события. Этот флаг предназначен для использования главным образом с точки трассировки.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Используется ядро отладчика машинного кода, чтобы определить, следует ли очистить состояние обхода. Он отличается от BP90_FLAG_DONT_STOP, так как BP90_FLAG_DONT_STOP не задается, если макрос выполняет точка трассировки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)