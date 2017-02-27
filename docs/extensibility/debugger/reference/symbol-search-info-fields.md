---
title: "SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление SYMBOL_SEARCH_INFO_FIELDS"
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SYMBOL_SEARCH_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает тип данных о символах извлечь.  
  
## Синтаксис  
  
```cpp#  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```c#  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## Члены  
 SSIF\_NONE  
 Указывает флаги нет  
  
 SSIF\_VERBOSE\_SEARCH\_INFORMATION  
 Возвращает все пути поиска, используемые для поиска символов  
  
## Заметки  
 Эти флаги передаются как параметр [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) метод позволяет определить возвращаемое количество информации.  
  
> [!NOTE]
>  В настоящее время только `SSIF_VERBOSE_SEARCH_INFO` поддерживается и должен быть определен как  `dwFlags` параметр  `IDebugModule3::GetSymbolInfo`.  Все остальные значения, возвращают ошибку.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)