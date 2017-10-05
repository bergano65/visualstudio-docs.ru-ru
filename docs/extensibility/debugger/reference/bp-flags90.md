---
title: "BP_FLAGS90 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e958be77ca266af30556fa8c03c580eea94b903
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

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
