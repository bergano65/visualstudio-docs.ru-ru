---
title: Проекты гнездования Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707030"
---
# <a name="nesting-projects"></a>Проекты вложения
Разработчики корпоративных приложений, использующие ваш пакет VS, могут удобно группировать подобные типы проектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] вместе, используя *вложение проектов.* Например, проект Enterprise Template использует вложенные проекты для группы проектов в категории. Проекты бизнес-фасада, веб-проекты uI и так далее сгруппированы в одну категорию.

 В этом сценарии нет ограничений на количество проектов, которые разработчик может приложить в рамках каждого родительского проекта, хотя разработчик может программно предоставлять ограничения. Этот тип группировки также может быть рекурсивным, и в этом случае проекты того же типа, что и проект ребенка, могут быть вложены под ребенка, чтобы стать подпроектом ребенка, который является подпроектом родителя.

 Проект гнездования не является неотъемлемой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]частью . Вы должны написать код, чтобы вложение и подпроект вложения в рамках детских проектов. Родительский проект представляет собой специальный VSPackage, или тип проекта, созданный и зарегистрированный с его собственным GUID, который включает в себя код, необходимый для реализации вложения проекта.

 Вы можете найти пример о том, как гнездить проекты в [Как: Реализация вложенных проектов.](../../extensibility/internals/how-to-implement-nested-projects.md)

## <a name="nested-projects-example"></a>Пример вложенных проектов
 ![Решение nested Projects](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Пример вложенных проектов

## <a name="see-also"></a>См. также
- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Параметры контекста](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
