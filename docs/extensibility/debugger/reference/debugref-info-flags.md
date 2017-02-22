---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
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
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "Перечисление DEBUGREF_INFO_FLAGS"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает, какую информацию, которую необходимо извлечь об объекте ссылки отладки.  
  
## Синтаксис  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Члены  
 DEBUGREF\_INFORMATION\_NAME  
 Инициализируйте и использование `bstrName` поля в макете.  
  
 DEBUGREF\_INFORMATION\_TYPE  
 Инициализируйте и использование `bstrType` поля в макете.  
  
 DEBUGREF\_INFORMATION\_VALUE  
 Инициализируйте и использование `bstrValue` поля в макете.  
  
 DEBUGREF\_INFORMATION\_ATTRIB  
 Инициализируйте и использование`dwAttrib` поля в макете.  
  
 DEBUGREF\_INFORMATION\_REFTYPE  
 Инициализируйте и использование `dwRefType` поля в макете.  
  
 DEBUGREF\_INFORMATION\_REF  
 Инициализируйте и использование `pReference` поля в макете.  
  
 DEBUGREF\_INFORMATION\_VALUE\_AUTOEXPAND  
 Поле должно содержать значения автоматическ\-развернутое значение, если он доступен для данного типа объекта.  
  
 DEBUGREF\_INFORMATION\_NONE  
 Указывает, что флаги не заданы.  
  
 DEBUGREF\_INFORMATION\_ALL  
 Указывает маску флагов.  
  
## Заметки  
 Эти флаги передаются [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) и  [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) методы, чтобы показать, какие поля  [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура быть инициализированным.  
  
 Используется для `dwFields` элемент  `DEBUG_REFERENCE_INFO` структура, чтобы показать, какие поля используются и допустимы, если структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)