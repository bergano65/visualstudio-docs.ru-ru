---
title: "DEBUG_ADDRESS | Microsoft Docs"
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
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "Структура DEBUG_ADDRESS"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура представляет адрес.  
  
## Синтаксис  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## Термины  
 ulAppDomainID  
 Идентификатор процесса  
  
 guidModule  
 Идентификатор GUID модуля, содержащего этот адрес.  
  
 tokClass  
 Токен, задав класс или тип адреса.  
  
> [!NOTE]
>  Это значение поставщику символов и поэтому не имеет смысл смысл как общий, отличный от идентификатора для типа класса.  
  
 addr  
 A [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структура, которая содержит объединение структур, которые описывают отдельные типы адреса.  Значение `addr`.`dwKind` поступает из  [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисление, которое объясняет, как интерпретировать соединение.  
  
## Заметки  
 Эта структура передается [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод, который требуется заполнить.  
  
 **Предупреждение только \[C\+\+\]**  
  
 If `addr.dwKind` существует  `ADDRESS_KIND_METADATA_LOCAL` и  `addr.addr.addrLocal.pLocal` имеет значение NULL, необходимо вызвать  `Release` указателя токена:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)