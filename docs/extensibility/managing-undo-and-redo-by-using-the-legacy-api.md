---
title: "Управление отмены и повтора с помощью API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - отменить управления"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Управление отмены и повтора с помощью API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редакторы должны поддерживать операции отмены, позволяющих пользователям отменить их последние изменения, когда они изменять код. Большинство редакторов, реализованных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] может иметь поддержка функции отмены, автоматически предоставляемые интегрированную среду разработки \(IDE\).  
  
## В этом подразделе  
 [Практическое руководство: реализация управления отмены](../extensibility/how-to-implement-undo-management.md)  
 Предоставляет возможность отмены изменений для редакторов с одним или несколькими представлениями.  
  
 [Практическое руководство: Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)  
 Описывается, как очистить стек отмены.  
  
 [Практическое руководство: использование управления связанный откат](../extensibility/how-to-use-linked-undo-management.md)  
 Включает управление связанный откат в редактор.  
  
## Ссылка  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Предоставляет редактор, который поддерживает несколько представлений управления отмены.  
  
## Связанные подразделы