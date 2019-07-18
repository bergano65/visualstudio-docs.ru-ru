---
title: Управление отменять и повторять с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194360"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Управление операциями "Отменить" и "Повторить" с помощью API прежних версий
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
