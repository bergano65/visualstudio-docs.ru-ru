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
ms.openlocfilehash: bb2ff049635d75608114be380c9697faf0585725
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177896"
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

