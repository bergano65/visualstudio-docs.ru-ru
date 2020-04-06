---
title: Добавление шаблонов элементов проекта и проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710197"
---
# <a name="add-project-and-project-item-templates"></a>Добавление шаблонов элементов проекта и проекта
При создании собственных типов проектов необходимо обеспечить поддержку добавления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] новых проектов и элементов проекта с помощью стандартных диалогов ы интегрированной среды разработки (IDE). Следующие темы обсуждают различные методы добавления проектов и элементов проекта.

## <a name="in-this-section"></a>В этом разделе
- [Контекст проекта](../../extensibility/internals/project-context.md)

 Объясняет, что проект предоставляет большую часть контекстной информации для того, что происходит в среде.

- [Приоритет проекта](../../extensibility/internals/project-priority.md)

 Объясняет, что элемент проекта обычно является участником одного проекта, чтобы избежать двусмысленности того, какой проект используется для открытия элемента.

- [Проект «Разные файлы»](../../extensibility/internals/miscellaneous-files-project.md)

 Предоставляет информацию о двух типах редакторов, которые могут быть использованы для открытия файлов в проекте, и о роли, которую проект играет в определении того, какой редактор использовать при открытии элемента проекта.

- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)

 Объясняет, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] происходит при создании проекта.

- [Добавление элементов в диалоговую окно Добавить новый элемент](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Объясняет процесс добавления элементов в диалоговую окно **Добавить новый элемент.**

- [Добавление каталогов в поле диалога нового проекта](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Приводит пример регистрации нового каталога, содержащего пользовательские шаблоны, доступные VSPackage.

- [Добавить каталоги в диалоговую коробку Добавить новый элемент](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Приводит пример регистрации нового набора каталогов для диалогового окна **Add New Item.**

- [Определяющие IDE команды для расширения проектных систем](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Перечисляет различные типы командных элементов, используемых для расширения проектных систем.

- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Перечисляет CATID для объектов, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]которые [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] используются для расширения, и проектных систем.

## <a name="related-sections"></a>См. также
- [Как: Открыть редакторы для конкретных проектов](../../extensibility/how-to-open-project-specific-editors.md)

 Предоставляет пошаговые инструкции по открытию элемента, присущего конкретному редактору проекта.

- [Как: Открытые стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)

 Предоставляет пошаговые инструкции по открытию стандартного редактора.

- [Подтипы проекта](../../extensibility/internals/project-subtypes.md)

 Предоставляет ссылки на концептуальные темы подтипа проекта. Подтипы проектов расширяют существующие [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекты.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Предоставляет ссылки на дополнительные темы, которые предлагают информацию о том, как разрабатывать новые типы проектов.
