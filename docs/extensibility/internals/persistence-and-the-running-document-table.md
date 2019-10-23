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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726085"
---
# <a name="persistence-and-the-running-document-table"></a>Сохранение состояния и запуск таблицы документов
В интегрированной среде разработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты полностью отвечают за управление сохраняемостью элементов проекта, которые они выполняют с помощью службы, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Документы являются базовой единицей сохраняемости в среде Visual Studio. Проекты координируют время на открытие, сохранение и переименование документов с помощью выполняемой таблицы документов (РДТ) — ресурса, который отслеживает состояние всех открытых документов.

## <a name="managing-persistence"></a>Управление сохраняемостью
 Проекты управляют службой сохраняемости среды, реализуя интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>. Хотя среда никогда не запрашивает документ для сохранения, он запрашивает проект-владелец (или иерархию) для сохранения документа. Это позволяет проекту сохранять данные элементов проекта в локальные файлы, удаленные файлы, базу данных, репозиторий или другой носитель.

 Глобальная среда поддерживает РДТ. Среда сохраняет записи для всех открытых окон и документов в РДТ, что позволяет им получать специальные уведомления, например, когда решение закрыто. Кроме того, РДТ позволяет среде отслеживанию соответствующих узлов в **Обозреватель решений**. РДТ поддерживает одну запись для каждого открытого, сохраняемого объекта, включая файлы проекта и документы элементов проекта.

## <a name="see-also"></a>См. также
- [Запуск таблицы документов](../../extensibility/internals/running-document-table.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)