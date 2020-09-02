---
title: Управление отменой и повтором с помощью API прежних версий | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194360"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Управление операциями "Отменить" и "Повторить" с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редакторы должны поддерживать операции отмены, которые позволяют пользователям менять свои последние изменения при изменении кода. Большинство редакторов, реализованных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] могут иметь поддержку отмены, автоматически предоставляемую интегрированной средой разработки (IDE).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Практическое руководство. Реализация управления отменой](../extensibility/how-to-implement-undo-management.md)  
 Предоставляет возможность отмены для редакторов с одним или несколькими представлениями.  
  
 [Практическое руководство. Очистка стека отмены](../extensibility/how-to-clear-the-undo-stack.md)  
 Описание очистки стека отмены.  
  
 [Практическое руководство. Использование управления связанной отменой](../extensibility/how-to-use-linked-undo-management.md)  
 Включает в редактор связанное управление отменой.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Предоставляет механизмы управления отменой для редактора, поддерживающие несколько представлений.  
  
## <a name="related-sections"></a>См. также
