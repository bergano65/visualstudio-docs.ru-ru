---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "Перечисление FIELD_MODIFIERS"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает модификаторы для типа поля.  
  
## Синтаксис  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Члены  
 FIELD\_MOD\_ACCESS\_TYPE  
 Указывает, что поле нельзя получить доступ.  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 Указывает, что поле имеет открытый доступ.  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 Указывает, что поле защищало доступ.  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 Указывает, что для поля задан закрытый доступ.  
  
 FIELD\_MOD\_NOMODIFIERS  
 Указывает, что поле отсутствуют модификаторы.  
  
 FIELD\_MOD\_STATIC  
 Указывает, что поле является статическим.  
  
 FIELD\_MOD\_CONSTANT  
 Указывает, что поле является константой.  
  
 FIELD\_MOD\_TRANSIENT  
 Указывает, что поле переходно.  
  
 FIELD\_MOD\_VOLATILE  
 Указывает, что поле испаряюще.  
  
 FIELD\_MOD\_ABSTRACT  
 Указывает, что поле является абстрактным.  
  
 FIELD\_MOD\_NATIVE  
 Указывает, что поле собственно.  
  
 FIELD\_MOD\_SYNCHRONIZED  
 Указывает, что поле синхронизирована.  
  
 FIELD\_MOD\_VIRTUAL  
 Указывает, что поле является виртуальным.  
  
 FIELD\_MOD\_INTERFACE  
 Указывает, что поле интерфейс.  
  
 FIELD\_MOD\_FINAL  
 Указывает, что поле окончательное.  
  
 FIELD\_MOD\_SENTINEL  
 Указывает, что поле часовой.  
  
 FIELD\_MOD\_INNERCLASS  
 Указывает, что поле внутренний класс.  
  
 FIELD\_TYPE\_OPTIONAL  
 Указывает, что поле является необязательным.  
  
 FIELD\_MOD\_BYREF  
 Указывает, что поле аргумент ссылки.  Это специально для аргументов метода.  
  
 FIELD\_MOD\_HIDDEN  
 Указывает, что поле должно скрывать или представить в другом контексте. например, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] статические локальные переменные.  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 Указывает, что поле представляет объект с `IUnknown` интерфейс.  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 Указывает, что поле имеет специальное имя, например `.ctor` для конструктора \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только\).  
  
 FIELD\_MOD\_HIDEBYSIG  
 Указывает, что для поля задан `Overloads` ключевое слово, примененное к нему \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только\).  
  
 FIELD\_MOD\_WRITEONLY  
 Указывает, что поле доступно только на запись.  Это значение не включается в пределах `FIELD_MOD_ALL`использование таких как линия, доступных только на запись полей для вычисления функции.  Пользователь должен явно запросить `FIELD_MOD_WRITEONLY` поля.  
  
 FIELD\_MOD\_ACCESS\_MASK  
 Указывает маску для доступа к полю.  
  
 FIELD\_MOD\_MASK  
 Указывает маску модификаторы для поля.  
  
## Заметки  
 Используется для `dwModifiers` элемент  [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) структура.  
  
 Эти значения также передаются [EnumFields](../Topic/IDebugContainerField::EnumFields.md) метод, для которого следует выполнить фильтрацию определенных полей.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../Topic/IDebugContainerField::EnumFields.md)