---
title: Поддержка мастера для вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721424"
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
В интегрированной среде разработки выполняются два мастера, которые может реализовать родительский проект для вложенных проектов: мастер **создания проекта** и мастер **добавления элемента** .

 Если пользователь запускает мастер **создания проекта** , выбрав пункт **Добавить проект** и выбрав пункт **создать проект** в меню файл или выбрав **Добавить** и щелкнув правой кнопкой мыши **Новый проект** в Обозреватель решений, в интегрированной среде разработки выполняется **аддпрожект.** команда и реализация родительского проекта команды **аддпрожект** либо возвращают файл проекта шаблона, либо файл мастера (VSZ) с набором параметров контекста.

 Аналогичным образом реализация мастеров **AddItem** в родительском проекте возвращает VSZ-файл с другим набором параметров контекста.

 Дополнительные сведения о мастерах см. в разделе [Мастер (. VSZ) файл](../../extensibility/internals/wizard-dot-vsz-file.md), [Параметры контекста](../../extensibility/internals/context-parameters.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)