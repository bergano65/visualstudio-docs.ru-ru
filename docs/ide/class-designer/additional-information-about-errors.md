---
title: Ошибки конструктора классов
description: Сведения о том, как разрешать ошибки конструктора классов путем перетаскивания измененного или перемещенного исходного кода в диаграмму классов для его отображения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575f9b74c7931ecc752f4c2e56866534aaa1e3d5
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903108"
---
# <a name="class-designer-errors"></a>Ошибки конструктора классов

**Конструктор классов** не отслеживает расположение исходных файлов, поэтому изменение структуры проекта или перемещение исходных файлов в проекте может привести к тому, что **конструктор классов** не будет отслеживать тип (например, часто изменяются исходный тип определения типов, базовые классы или типы связей). Может возникнуть ошибка, например **Конструктору классов не удалось отобразить этот тип**. Для исправления этой ошибки снова перетащите измененный или перемещенный исходный код в схему классов, чтобы отобразить изменения.

## <a name="resources"></a>Ресурсы

Вы можете получить помощь по другим ошибкам и предупреждениям в следующих ресурсах:

- [Работа с кодом Visual C++](working-with-visual-cpp-code.md) Содержит сведения об устранении неполадок при отображении C++ на схеме классов.
- [Форум по конструктору классов Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) предназначен для вопросов по работе с **конструктором классов**.

## <a name="see-also"></a>См. также раздел

- [Разработка и просмотр классов и типов](designing-and-viewing-classes-and-types.md)
