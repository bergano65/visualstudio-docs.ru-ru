---
title: Управление отменять и повторять с помощью API прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab655c4822f7f5186cbcd18d451cfa3bb0aa656e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764178"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Управление отмены и повтора с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редакторы должен поддерживать операции отмены, которые пользователи могут отменить их последние изменения в том случае, если изменят код. Большинство редакторов, реализованных в разделе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] может иметь возможность отмены изменений, автоматически предоставляемых интегрированной среде разработки (IDE).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Реализация управления отменой](../extensibility/how-to-implement-undo-management.md)  
 Предоставляет возможность отмены изменений для редакторов с одним или несколькими представлениями.  
  
 [Практическое руководство. Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)  
 Описывает, как очистить стек отмены.  
  
 [Практическое руководство. Использование управления связанной отменой](../extensibility/how-to-use-linked-undo-management.md)  
 Включает связанный откат управления в редакторе.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Предоставляет механизмы управления отменой для редактора, который поддерживает несколько представлений.  
  
## <a name="related-sections"></a>Связанные разделы

