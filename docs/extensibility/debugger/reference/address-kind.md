---
title: "ADDRESS_KIND | Microsoft Docs"
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
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "Перечисление ADDRESS_KIND"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет типы адресов.  
  
## Синтаксис  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## Термины  
 ADDRESS\_KIND\_NATIVE  
 Собственный адрес, представленный  [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) структура.  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 Неуправляемый адрес по отношению к a `this` \(`Me` в указателе Visual Basic\) и представляется  [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) структура.  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 Автономный физический адрес, представленный  [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) структура.  
  
 ADDRESS\_KIND\_METHOD  
 Метод класса, представленного [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) структура.  
  
 ADDRESS\_KIND\_FIELD  
 Поля класса, представленное [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) структура.  
  
 ADDRESS\_KIND\_LOCAL  
 Адрес локальной переменной и представляется [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) структура.  
  
 ADDRESS\_KIND\_PARAM  
 Параметр метода или функции, представленный  [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) структура.  
  
 ADDRESS\_KIND\_ARRAYELEM  
 Элемент массива, представленный  [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) структура.  
  
 ADDRESS\_KIND\_RETVAL  
 Возвращаемое значение, представленное  [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) структура.  
  
## Заметки  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод возвращает  [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура, содержащая объединение возможных структур  [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структура.  `dwKind` поле   `DEBUG_ADDRESS_UNION` структура сохраняет  `ADDRESS_KIND` значение и описывает способ интерпретации поле соединения.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)