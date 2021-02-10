---
title: Поддержка мастера для вложенных проектов | Документация Майкрософт
description: Узнайте о двух мастерах, которые Родительский проект может реализовать для вложенных проектов в VSPackage в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f2cd84379ead1cd45296ae370aab215a37cf4b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935875"
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
В интегрированной среде разработки выполняются два мастера, которые может реализовать родительский проект для вложенных проектов: мастер **создания проекта** и мастер **добавления элемента** .

 Если пользователь запускает мастер **создания проекта** , выбрав пункт **Добавить проект** и выбрав пункт **создать проект** в меню файл или выбрав пункт **Добавить** и щелкнув правой кнопкой мыши **Новый проект** в Обозреватель решений, интегрированная среда разработки выполнит команду **аддпрожект** , а реализация команды **аддпрожект** в родительском проекте вернет файл проекта шаблона или мастер (VSZ-файл) с набором параметров контекста.

 Аналогичным образом реализация мастеров **AddItem** в родительском проекте возвращает VSZ-файл с другим набором параметров контекста.

 Дополнительные сведения о мастерах см. в разделе [Мастер (. VSZ) файл](../../extensibility/internals/wizard-dot-vsz-file.md), [Параметры контекста](../../extensibility/internals/context-parameters.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)
