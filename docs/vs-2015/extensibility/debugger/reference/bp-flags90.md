---
title: BP_FLAGS90 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153494"
---
# <a name="bp_flags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет допустимые значения для необязательных флагов. Необязательные флаги можно использовать для указания дополнительных сведений при задании точки останова. Это перечисление расширяет перечисление [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Указывает отсутствие флага точки останова.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Указывает, что модуль отладки (DE) должен сопоставлять точку останова, используя расположение документа. Это применимо только к точкам останова, заданным в исходных файлах, ориентированных на скрипт, например Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Указывает, что точка останова должна обрабатываться модулем отладки, но в конечном итоге отладчик не должен останавливаться. то есть объект события [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не должен отправляться. Этот флаг предназначен для использования в основном с точками трассировки.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Используется модулем отладки машинного кода для определения, следует ли очищать состояние пошагового выполнения. Он отличается от BP90_FLAG_DONT_STOP, поскольку BP90_FLAG_DONT_STOP не задан, если точка трассировки выполняет макрос.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
