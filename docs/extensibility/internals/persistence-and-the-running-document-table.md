---
title: Настойчивость и таблица «Запуск документов» (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706722"
---
# <a name="persistence-and-the-running-document-table"></a>Сохранение состояния и запуск таблицы документов
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, проекты полностью отвечают за управление сохранением своих элементов <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>проекта, которые они выполняют с помощью службы, . Документы являются основной единицей настойчивости в среде Visual Studio. Проекты координируют открытие, сохранение и переименование документов с таблицей запущенных документов (RDT), ресурсом, который отслеживает состояние всех открытых документов.

## <a name="managing-persistence"></a>Управление настойчивостью
 Проекты контролируют службу сохранения среды, реализуя <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> интерфейс. Хотя среда никогда непосредственно не запрашивает сам документ, она просит проект владения (или иерархию) сохранить документ. Это позволяет проекту сохранять данные элемента проекта в локальных файлах, удаленных файлах, базе данных, репозитории или другом носителе.

 Глобальная окружающая среда поддерживает RDT. Среда поддерживает записи для всех открытых окон и документов в RDT, что позволяет им получать специальные уведомления, например, когда решение закрыто. Кроме того, RDT позволяет окружающей среде отслеживать соответствующие узлы в **Solution Explorer.** RDT поддерживает одну запись на открытый, сохраняемый объект, включая как файлы проекта, так и документы проекта.деталь.

## <a name="see-also"></a>См. также
- [Запуск таблицы документов](../../extensibility/internals/running-document-table.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)
