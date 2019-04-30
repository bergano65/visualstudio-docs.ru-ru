---
title: Управление отменять и повторять с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856424"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Управление отмены и повтора с помощью предыдущих версий API
Редакторы должен поддерживать операции отмены, которые пользователи могут отменить их последние изменения в том случае, если изменят код. Большинство редакторов, реализованных в разделе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] может иметь возможность отмены изменений, автоматически предоставляемых интегрированной среде разработки (IDE).

## <a name="in-this-section"></a>Содержание раздела
- [Практическое руководство. Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md) предоставляет возможность отмены изменений для редакторов с одним или несколькими представлениями.

- [Практическое руководство. Очистить стек отмены](../extensibility/how-to-clear-the-undo-stack.md) описывается, как очистить стек отмены.

- [Практическое руководство. Используйте Управление связанный откат](../extensibility/how-to-use-linked-undo-management.md) Incorporates связанные механизмы управления отменой в редактор.

## <a name="reference"></a>Ссылка
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Предоставляет механизмы управления отменой для редактора, который поддерживает несколько представлений.
