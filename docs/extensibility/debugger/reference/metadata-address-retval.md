---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "Структура METADATA_ADDRESS_RETVAL"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура представляет значение, возвращаемое из метода или функции.  
  
## Синтаксис  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## Термины  
 tokMethod  
 Идентификатор метода это возвращаемое значение —.  
  
 dwCorType  
 Базовый тип возвращаемого значения. Это значение из `CorElementType` перечисление, определенное в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] файле corhdr.h SDK.  
  
 dwSigSize  
 Размер подписи возвращаемое значение \(хранящихся в `rgSig`\).  
  
 rgSig  
 Массив байтов, формирующие сигнатуры, возвращаемого значения.  
  
## Заметки  
 Эта структура является частью объединения в [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры при `dwKind` поле `DEBUG_ADDRESS_UNION` структуры задано значение `ADDRESS_KIND_RETVAL` \(значение из [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления\).  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)