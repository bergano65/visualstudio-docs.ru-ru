---
title: Сохраняемость и выполняемая таблица документов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706722"
---
# <a name="persistence-and-the-running-document-table"></a>Сохранение состояния и запуск таблицы документов
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки проекты полностью отвечают за управление сохраняемостью элементов проекта, которые они выполняют с помощью службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Документы являются базовой единицей сохраняемости в среде Visual Studio. Проекты координируют время на открытие, сохранение и переименование документов с помощью выполняемой таблицы документов (РДТ) — ресурса, который отслеживает состояние всех открытых документов.

## <a name="managing-persistence"></a>Управление сохраняемостью
 Проекты управляют службой сохраняемости среды путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> интерфейса. Хотя среда никогда не запрашивает документ для сохранения, он запрашивает проект-владелец (или иерархию) для сохранения документа. Это позволяет проекту сохранять данные элементов проекта в локальные файлы, удаленные файлы, базу данных, репозиторий или другой носитель.

 Глобальная среда поддерживает РДТ. Среда сохраняет записи для всех открытых окон и документов в РДТ, что позволяет им получать специальные уведомления, например, когда решение закрыто. Кроме того, РДТ позволяет среде отслеживанию соответствующих узлов в **Обозреватель решений**. РДТ поддерживает одну запись для каждого открытого, сохраняемого объекта, включая файлы проекта и документы элементов проекта.

## <a name="see-also"></a>См. также раздел
- [Запуск таблицы документов](../../extensibility/internals/running-document-table.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)
