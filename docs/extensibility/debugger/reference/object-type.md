---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "Перечисление OBJECT_TYPE"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает тип объекта в средстве оценки выражений.  
  
## Синтаксис  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Члены  
 OBJECT\_TYPE\_BOOLEAN  
 Указывает, что объект является логическое значение.  
  
 OBJECT\_TYPE\_CHAR  
 Указывает, что объект является символ.  
  
 OBJECT\_TYPE\_I1  
 Указывает, что объект знаковое целое число одн\-байта.  
  
 OBJECT\_TYPE\_U1  
 Указывает, что объект является целое число без знака одн\-байта.  
  
 OBJECT\_TYPE\_I2  
 Указывает, что объект двубайтовое знаковое целое число.  
  
 OBJECT\_TYPE\_U2  
 Указывает, что объект двубайтовое целое число без знака.  
  
 OBJECT\_TYPE\_I4  
 Указывает, что объект знаковое целое число 4 байта.  
  
 OBJECT\_TYPE\_U4  
 Указывает, что объект является целое число без знака длиной 4 байта.  
  
 OBJECT\_TYPE\_I8  
 Указывает, что объект знаковое целое число 8 байта.  
  
 OBJECT\_TYPE\_U8  
 Указывает, что объект является целое число без знака длиной 8 байта.  
  
 OBJECT\_TYPE\_R4  
 Указывает, что объект число с плавающей запятой длиной 4 байта.  
  
 OBJECT\_TYPE\_R8  
 Указывает, что объект число с плавающей запятой длиной 8 байта.  
  
 OBJECT\_TYPE\_OBJECT  
 Указывает, что объект является объектом.  
  
 OBJECT\_TYPE\_NULL  
 Указывает, что объект значение null.  
  
 OBJECT\_TYPE\_CLASS  
 Указывает, что объект класса.  
  
## Заметки  
 Передается в качестве аргумента [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) и  [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) методы.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)