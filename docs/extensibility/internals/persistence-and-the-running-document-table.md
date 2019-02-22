---
title: Сохранение и выполнение документа таблицы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: deb5472776bc9c4a4d6bb0ccd8830cba5eea3d04
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640273"
---
# <a name="persistence-and-the-running-document-table"></a>Сохранение состояния и запуск таблицы документов
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки, проекты полностью отвечаете за проведение сохраняемость элементов проектов, которые они выполняют, с помощью службы, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Документы являются базовой единицей сохраняемости в среде Visual Studio. Проекты координировать открытие, сохранение и переименование документов в таблице выполняющихся документов (RDT), ресурс, который отслеживает состояние всех открытых документах.

## <a name="managing-persistence"></a>Управление сохраняемости
 Проекты управления среды службы постоянного хранения, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> интерфейс. Хотя среды напрямую никогда не запрашивает документ для сохранения сам, запрашивает у владельца проекта (или иерархии) для сохранения документа. Это позволяет для проекта сохранить данные элемента проекта в локальные файлы, удаленные файлы, базы данных, репозитория или другой носитель.

 Глобальные среды поддерживает RDT. Среды поддерживает записи для всех открытых окон и документы в RDT, что делает возможным их получать специальные уведомления, например при закрытии решения. Кроме того, RDT делает возможным для среды, чтобы отслеживать их соответствующими узлами **обозревателе решений**. RDT хранит одну запись для каждой открытой, сохраняемого объекта, включая файлы проектов и элементов проекта документов.

## <a name="see-also"></a>См. также
- [Запуск таблицы документов](../../extensibility/internals/running-document-table.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)