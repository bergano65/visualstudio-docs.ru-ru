---
title: "IntelliSenseHostFlags | Microsoft Docs"
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
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "Технология IntelliSense, перечисление IntellisenseHostFlags"
  - "Перечисление IntellisenseHostFlags"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает флаги узла IntelliSense.  
  
## Синтаксис  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### Параметры  
  
|Участники|Описание|  
|---------------|--------------|  
|`IHF_READONLYCONTEXT`|Контекст буфер доступен только для чтения.|  
|`IHF_NOSEPARATESUBJECT`|Текст без темы. Контекст буфер содержит целевой IntelliSense \(подразумевает `!IHF_READONLYCONTEXT`\).|  
|`IHF_SINGLELINESUBJECT`|Текст темы не несколькими\-строки поддерживает.|  
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Изменение \(в теме или контекста\) должно выполняться в режиме замены.|  
  
## Требования  
 SingleFileeditor.idl  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>