---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление FIELD_INFO_FIELDS"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает, какую информацию для получения собирается IDebugField объект.  
  
## Синтаксис  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Члены  
 FIF\_FULLNAME  
 Инициализируйте и использование `bstrFullName` поле  [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) структура.  
  
 FIF\_NAME  
 Инициализируйте и использование `bstrName` поле  `FIELD_INFO` структура.  
  
 FIF\_TYPE  
 Инициализируйте и использование `bstrType` поле  `FIELD_INFO` структура.  
  
 FIF\_MODIFIERS  
 Инициализируйте и использование `bstrModifiers` поле  `FIELD_INFO` структура.  
  
## Заметки  
 Эти значения также передаются в качестве аргумента [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) метод, чтобы указать, какие поля  [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) структура быть инициализированным.  
  
 Эти значения также используются в `dwFields` элемент  `FIELD_INFO` структура для указания того, какие поля используются и допустимы.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)