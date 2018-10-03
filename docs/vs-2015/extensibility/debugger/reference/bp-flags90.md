---
title: BP_FLAGS90 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c983356d3a808d523ddd8a5cb87912f0a2638d7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570365"
---
# <a name="bpflags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [BP_FLAGS90](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-flags90).  
  
Перечисляет допустимые значения для необязательные флаги. Необязательные флаги может использоваться для указания дополнительных сведений, если установить точку останова. Это перечисление расширяет [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисления.  
  
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
 Задает флаг без точки останова.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Указывает, что модуль отладки (DE) следует сопоставить точку останова с помощью позиции документа. Это значение применимо только к точки останова в скрипт ориентированного исходных файлов таких как Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Указывает, что точка останова должны обрабатываться с помощью обработчика отладки, но что модуль отладки в конечном счете следует останавливает существует; то есть [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не следует отправлять объект события. Этот флаг предназначен для использования главным образом с точки трассировки.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Чтобы определить, следует ли очистить состояние пошагового выполнения, используемые ядром отладки машинного кода. Он отличается от BP90_FLAG_DONT_STOP, так как BP90_FLAG_DONT_STOP не задается, если макрос выполняет точки трассировки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

