---
title: Поддержка мастера для вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fd9871e794c2968bab3effce0717ea1cae508eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603968"
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
Интегрированная среда разработки выполняет два мастера, которые можно реализовать в родительский проект для вложенных проектов: **новый проект** мастера и **Добавление элемента** мастера.

 Если пользователь запускает **новый проект** мастера, выбрав **добавить проект** и щелкнув **новый проект** в меню "файл" или выбрав **добавить** и щелкните правой кнопкой мыши **новый проект** в обозревателе решений в IDE выполняется **AddProject** команда и реализация в родительский проект **AddProject**команда возвращает либо файл шаблона проекта или файл мастера (VSZ), содержащий набор параметров контекста.

 Точно так же родительском проекте реализации **AddItem** мастеров возвращает VSZ-файл, который имеет отдельный набор параметров контекста.

 Дополнительные сведения о мастерах см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [параметры контекста](../../extensibility/internals/context-parameters.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)