---
title: Поддержка Волшебника для вложенных проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703193"
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
IDE запускает два мастера, которые может реализовать родительский проект для вложенных проектов: мастер **нового проекта** и мастер **добавить элемент.**

 Если пользователь запускает мастер створ **нового проекта,** выбрав **Add Project** и нажав **New Project** в меню файла или выбрав **добавить** и нажав **на кнопку New Project** в Solution Explorer, IDE запускает команду **AddProject** и реализацию родительского проекта команды **AddProject** либо возвращает файл шаблона проекта, либо файл мастера (.vsz), который имеет набор параметров контекста.

 Аналогичным образом, реализация родительским проектом мастеров **AddItem** возвращает файл .vsz с другим набором параметров контекста.

 Для получения дополнительной информации о мастерах, [см. Vsz) Файл](../../extensibility/internals/wizard-dot-vsz-file.md), [Параметры контекста](../../extensibility/internals/context-parameters.md) и [регистрации проекта и шаблонов элементов](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)
