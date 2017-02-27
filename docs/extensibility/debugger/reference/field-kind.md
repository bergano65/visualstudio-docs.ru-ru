---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "Перечисление FIELD_KIND"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет тип поля, содержащиеся в IDebugField объект.  
  
## Синтаксис  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Члены  
 FIELD\_KIND\_TYPE  
 Указывает, что поле тип.  
  
 FIELD\_KIND\_SYMBOL  
 Указывает, что поле символ, с типом, имя и другие сведения.  
  
 FIELD\_TYPE\_PRIMITIVE  
 Указывает, что поле является типом\-примитивом.  
  
 FIELD\_TYPE\_STRUCT  
 Указывает, что поле структуры.  
  
 FIELD\_TYPE\_CLASS  
 Указывает, что поля класса.  
  
 FIELD\_TYPE\_INTERFACE  
 Указывает, что поле интерфейс.  
  
 FIELD\_TYPE\_UNION  
 Указывает, что поле соединение.  
  
 FIELD\_TYPE\_ARRAY  
 Указывает, что поле массива.  
  
 FIELD\_TYPE\_METHOD  
 Указывает, что поле метод.  
  
 FIELD\_TYPE\_BLOCK  
 Указывает, что поле блок.  
  
 FIELD\_TYPE\_POINTER  
 Указывает, что поле указатель.  
  
 FIELD\_TYPE\_ENUM  
 Указывает, что поле тип перечислимые данных.  
  
 FIELD\_TYPE\_LABEL  
 Указывает, что поле метка.  
  
 FIELD\_TYPE\_TYPEDEF  
 Указывает, что поле typedef.  
  
 FIELD\_TYPE\_BITFIELD  
 Указывает, что поле bitfield.  
  
 FIELD\_TYPE\_NAMESPACE  
 Указывает, что поле пространство имен.  
  
 FIELD\_TYPE\_MODULE  
 Указывает, что поле модуль.  
  
 FIELD\_TYPE\_DYNAMIC  
 Указывает, что поле является динамическим.  
  
 FIELD\_TYPE\_PROP  
 Указывает, что поле свойство.  
  
 FIELD\_TYPE\_INNERCLASS  
 Указывает, что поле внутренний класс.  
  
 FIELD\_TYPE\_REFERENCE  
 Указывает, что поле ссылка.  
  
 FIELD\_TYPE\_EXTENDED  
 Зарезервировано для использования в будущем.  
  
 FIELD\_SYM\_MEMBER  
 Указывает, что поле является элементом.  
  
 FIELD\_SYM\_LOCAL  
 Указывает, что поле является локальным.  
  
 FIELD\_SYM\_PARAMETER  
 Указывает, что поле параметра.  
  
 FIELD\_SYM\_THIS  
 Указывает, что поле "это" указатель.  
  
 FIELD\_SYM\_GLOBAL  
 Указывает, что поле является глобальным.  
  
 FIELD\_SYM\_PROP\_GETTER  
 Указывает, что поле извлекает свойства.  
  
 FIELD\_SYM\_PROP\_SETTER  
 Указывает, что поле задает свойства.  
  
 FIELD\_SYM\_EXTENDED  
 Зарезервировано для использования в будущем.  
  
 FIELD\_KIND\_MASK  
 Указывает маску для типов полей.  
  
 FIELD\_TYPE\_MASK  
 Указывает маску для типов полей.  
  
 FIELD\_SYM\_MASK  
 Указывает маску для символа.  
  
## Заметки  
 Возвращается из вызова [GetKind](../Topic/IDebugField::GetKind.md) метод.  
  
 В зависимости от типа поля [QueryInterface](/visual-cpp/atl/queryinterface) может быть вызван на  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс дополнительные определенной формы интерфейса.  Например, если [GetKind](../Topic/IDebugField::GetKind.md) возвращает  `FIELD_TYPE_METHOD`можно затем вызвать метод  `QueryInterface` при I`DebugField` доступ  [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) интерфейс.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)