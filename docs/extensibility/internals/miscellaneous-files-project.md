---
title: Разное проект файлов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707099"
---
# <a name="miscellaneous-files-project"></a>Проект прочих файлов
Когда пользователь открывает элементы проекта, IDE присваивает проекту «Разные файлы» любые элементы, которые не являются участниками каких-либо проектов в решении.

 Проекты играют важную роль в определении того, какой редактор используется, когда пользователь открывает элемент проекта. Проект может быть разработан для открытия определенных файлов с помощью конкретного редактора проекта или стандартного редактора.

 Редактор, специфичный для конкретного проекта, обычно требует, чтобы пользователь знал специальные знания или использовал специальные интерфейсы проекта. Для получения дополнительной информации, [см.](../../extensibility/how-to-open-project-specific-editors.md)

 Стандартный редактор может открыть любой файл конкретного расширения в любом проекте. Пользователь может настроить некоторые стандартные редакторы, такие как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] текстовый редактор, для проектов, но при этом сохранить их публичный характер. Стандартные редакторы создаются <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> с помощью метода.

 Если ни один проект в решении не отвечает, что он может открыть элемент проекта, IDE предоставляет специальный проект под названием «Разные файлы», который открывает любой файл.

 Этот специальный проект предусматривает открытие файла вне контекста проекта. Во время обработки метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> проект «Разные файлы» всегда отвечает с очень низким приоритетом. Таким образом, проект «Разные файлы» всегда уступает любому проекту с более высоким приоритетом, который может открывать файлы.

 Проект «Разные файлы» не требует от пользователя явного создания с помощью диалогового окна **Нового проекта.** Кроме того, проект «Разные файлы» не постоянно управляет списком участников проекта. Он использует дополнительную функцию для записи списка самых последних используемых файлов для каждого пользователя.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)
- [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
