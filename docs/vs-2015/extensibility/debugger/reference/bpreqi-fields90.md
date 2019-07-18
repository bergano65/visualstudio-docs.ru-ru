---
title: BPREQI_FIELDS90 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97a38b4296668cb287f34e5b1afcbd7c90477011
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153209"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет допустимые значения, определяющие извлекаемого запроса точки останова. Это перечисление расширяет [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 BPREQI90_BPLOCATION  
 Инициализировать или использовать `bpLocation` (точки останова) поле [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 BPREQI90_LANGUAGE  
 Инициализировать или использовать `guidLanguage` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PROGRAM  
 Инициализировать или использовать `pProgram` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PROGRAMNAME  
 Инициализировать или использовать `bstrProgramName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_THREAD  
 Инициализировать или использовать `pThread` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_THREADNAME  
 Инициализировать или использовать `bstrThreadName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PASSCOUNT  
 Инициализировать или использовать `bpPassCount` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_CONDITION  
 Инициализировать или использовать `bpCondition` (условие точки останова) поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_FLAGS  
 Инициализировать или использовать `dwFlags` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_ALLOLDFIELDS  
 Инициализировать или использовать все поля для объекта `BP_REQUEST_INFO` структуры.  
  
 BPREQI90_VENDOR  
 Инициализировать или использовать `guidVendor` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_CONSTRAINT  
 Инициализировать или использовать `bstrConstraint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_TRACEPOINT  
 Инициализировать или использовать `bstrTracepoint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_MACROTRACEPOINT  
 Инициализировать или использовать `bstrMacroTracepoint` поле `BP_REQUEST_INFO2` структуры. BPREQI_ALLFIELDS не содержит этого поля.  
  
 BPREQI90_ALLFIELDS  
 Указывает все поля для `BP_REQUEST_INFO2` структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
