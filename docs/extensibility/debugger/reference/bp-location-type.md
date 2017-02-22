---
title: "BP_LOCATION_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "Структура BP_LOCATION_TYPE"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает тип расположения точки останова для запроса точки останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
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
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
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
  
## Члены  
 BPLT\_NONE  
 Не указывает местоположение точки останова.  
  
 BPLT\_FILE\_LINE  
 Указывает тип расположения точки останова в виде линии файла.  
  
 BPLT\_FUNC\_OFFSET  
 Указывает тип расположения точки останова в качестве смещения функций.  
  
 BPLT\_CONTEXT  
 Указывает тип расположения точки останова в качестве контекста.  
  
 BPLT\_STRING  
 Указывает тип расположения точки останова в виде строки.  
  
 BPLT\_ADDRESS  
 Указывает тип расположения точки останова в качестве адреса.  
  
 BPLT\_RESOLUTION  
 Указывает тип расположения точки останова, как разрешение.  
  
 BPLT\_CODE\_FILE\_LINE  
 Указывает тип расположения точки останова в виде линии исходного кода.  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 Указывает тип расположения точки останова в качестве смещения функций кода.  
  
 BPLT\_CODE\_CONTEXT  
 Указывает тип расположения точки останова в качестве контекста кода.  
  
 BPLT\_CODE\_STRING  
 Указывает тип расположения точки останова в виде строки кода.  
  
 BPLT\_CODE\_ADDRESS  
 Указывает тип расположения точки останова, как адрес кода.  
  
 BPLT\_DATA\_STRING  
 Указывает тип расположения точки останова в виде строки данных.  
  
 BPLT\_TYPE\_MASK  
 Указывает битовую маску, так что тип точки останова можно извлечь из значения.  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 Указывает битовую маску, так что тип расположения точки останова можно извлечь из значения.  
  
## Заметки  
 Передается как параметр [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) метод.  
  
 Тип расположения точки останова состоит из типа точки останова и тип расположения.  Это означает, что тип расположения точки останова не просто тип точки останова \(например,`BPT_CODE`\) или тип расположения \(например,`BPLT_FILE_LINE`\).  Предопределенные константы для всех, в настоящее время поддерживаемых типов расположения точки останова включены в этом перечислении \(`BPLT_CODE_FILE_LINE` via  `BPLT_DATA_STRING`\).  
  
 `BPT_CODE` и `BPT_DATA` являются членами перечисления [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)