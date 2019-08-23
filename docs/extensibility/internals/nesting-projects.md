---
title: Вложенные проекты | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289062a15c35641d5558409c7643301e346b6e65
ms.sourcegitcommit: f42b5318c5c93e2b5ecff44f408fab8bcdfb193d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976694"
---
# <a name="nesting-projects"></a>Проекты вложения
Разработчики корпоративных приложений, использующие пакет VS, могут группировать схожие типы проектов вместе [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью вложений *проектов*. Например, проект корпоративного шаблона использует вложенные проекты для группировки проектов по категориям. Проекты Business фасадной, проекты пользовательского веб-интерфейса и т. д. группируются в одной категории.

 В этом сценарии нет ограничений на количество проектов, которые разработчик может вкладывать в каждый родительский проект, хотя разработчик может программно предоставлять ограничения. Этот тип группирования можно также сделать рекурсивным. в этом случае проекты того же типа, что и дочерний проект, могут быть вложены в дочерний проект дочернего проекта, который является подпроектом родительского.

 Вложенность проектов не является встроенной частью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Необходимо написать код для включения вложенности и вложенных проектов в дочерних проектах. Родительский проект — это особый пакет VSPackage или тип проекта, созданный и зарегистрированный с собственным идентификатором GUID, включающий код, необходимый для реализации вложенности проекта.

 Пример вложения проектов [см. в следующих руководствах: Реализуйте вложенные проекты](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Пример вложенных проектов
 ![Решение вложенных проектов](../../extensibility/internals/media/vsnestedprojects.gif "вснестедпрожектс") Пример вложенных проектов

## <a name="see-also"></a>См. также
- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
