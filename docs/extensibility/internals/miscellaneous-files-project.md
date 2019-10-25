---
title: Проект прочих файлов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726676"
---
# <a name="miscellaneous-files-project"></a>Проект прочих файлов
Когда пользователь открывает элементы проекта, интегрированная среда разработки присваивает проекту Прочие файлы все элементы, которые не являются членами каких-либо проектов в решении.

 Проекты играют важную роль в определении того, какой редактор используется, когда пользователь открывает элемент проекта. Проект может быть разработан для открытия определенных файлов с помощью редактора конкретного проекта или стандартного редактора.

 Для конкретного проекта обычно требуется, чтобы пользователь имел специальные знания или использовал специальные интерфейсы из проекта. Дополнительные сведения см. [в разделе руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md).

 Стандартный редактор может открыть любой файл определенного расширения в любом проекте. Пользователь может настроить некоторые стандартные редакторы, такие как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] текстовый редактор, для проектов, но сохранили свои открытые символы. Стандартные редакторы создаются с помощью метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

 Если ни один из проектов в решении не реагирует на то, что он может открыть элемент проекта, интегрированная среда разработки предоставляет специальный проект с именем "Прочие файлы", который открывает любой файл.

 Этот специальный проект предоставляет для открытия файла вне контекста проекта. Во время обработки метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> проект прочих файлов всегда отвечает с очень низким приоритетом. Таким образом, проект "Прочие файлы" всегда возвращает любой проект с более высоким приоритетом, который может открывать файлы.

 В проекте "Прочие файлы" пользователь не должен явно создавать его с помощью диалогового окна " **Новый проект** ". Кроме того, проект прочих файлов не будет постоянно управлять списком членов проекта. Он использует необязательный компонент для записи списка последних использованных файлов для каждого пользователя.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)
- [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)