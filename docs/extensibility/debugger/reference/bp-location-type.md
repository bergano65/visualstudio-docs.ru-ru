---
title: BP_LOCATION_TYPE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db35e354b2cfbe91b9c6041dc6239d2dfd2531f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108947"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Указывает тип местоположения точки останова для запроса точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Участники  
 BPLT_NONE  
 Указывает нет точки останова.  
  
 BPLT_FILE_LINE  
 Указывает тип расположения точки останова, как строка файла.  
  
 BPLT_FUNC_OFFSET  
 Указывает тип расположения точки останова, как смещение функции.  
  
 BPLT_CONTEXT  
 Указывает тип расположения точки останова, как контекст.  
  
 BPLT_STRING  
 Указывает тип расположения точки останова в виде строки.  
  
 BPLT_ADDRESS  
 Указывает тип расположения точки останова, как адрес.  
  
 BPLT_RESOLUTION  
 Указывает тип расположения точки останова, как разрешение.  
  
 BPLT_CODE_FILE_LINE  
 Указывает тип расположения точки останова в строке исходного кода.  
  
 BPLT_CODE_FUNC_OFFSET  
 Указывает тип местоположения точки останова в виде смещения кода функции.  
  
 BPLT_CODE_CONTEXT  
 Указывает тип расположения точки останова, как контекст кода.  
  
 BPLT_CODE_STRING  
 Указывает тип расположения точки останова, как строка кода.  
  
 BPLT_CODE_ADDRESS  
 Указывает тип расположения точки останова, как адреса кода.  
  
 BPLT_DATA_STRING  
 Указывает тип расположения точки останова, как строка данных.  
  
 BPLT_TYPE_MASK  
 Указывает битовую маску, чтобы тип точки останова могут быть извлечены из значения.  
  
 BPLT_LOCATION_TYPE_MASK  
 Указывает битовую маску, чтобы тип местоположения точки останова могут быть извлечены из значения.  
  
## <a name="remarks"></a>Примечания  
 Переданное в качестве параметра для [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) метод.  
  
 Тип местоположения точки останова, состоит из тип точки останова и тип расположения. Это означает, что тип местоположения точки останова никогда не является типом точки останова (например, `BPT_CODE`) или тип расположения (например, `BPLT_FILE_LINE`). Предопределенные константы для всех типов расположение точки останова в настоящее время поддерживается включены в перечисление (`BPLT_CODE_FILE_LINE` через `BPLT_DATA_STRING`).  
  
 `BPT_CODE` и `BPT_DATA` являются членами [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисления.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)