---
title: Дополнительные сведения об ошибках конструктора классов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a095cd909dcd4d378fddc91c9151cf28e34a8ee5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852210"
---
# <a name="additional-information-about-class-designer-errors"></a>Дополнительные сведения об ошибках конструктора классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструктор классов не отслеживает расположение исходных файлов, поэтому, изменение структуры проекта или перемещение исходных файлов в проекте может привести к тому, что конструктор классов не будет отслеживать тип, особенно исходный тип для typedef, базовые классы или типы ассоциаций. Может возникнуть ошибка, например **Конструктору классов не удалось отобразить этот тип**. В этом случае перетащите измененный или перемещенный исходный код в схему классов и повторно отобразите ее.

 Вы можете получить помощь по другим ошибкам и предупреждениям в следующих ресурсах:

 [Работа с визуальным C++ кодом (конструктор классов)](../ide/working-with-visual-cpp-code-class-designer.md) включает сведения об устранении неполадок отображения C++ на схеме классов.

 [Форум по конструктору классов Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1) Форум предназначен для вопросов по работе с конструктором классов.

## <a name="see-also"></a>См. также
 [Разработка и просмотр классов и типов](../ide/designing-and-viewing-classes-and-types.md)
