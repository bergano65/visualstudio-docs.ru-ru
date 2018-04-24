---
title: Дополнительные сведения об ошибках конструктора классов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cd6223786db06506c1fa4ac9b6bd3118eb5e3d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="additional-information-about-class-designer-errors"></a>Дополнительные сведения об ошибках конструктора классов
Конструктор классов не отслеживает расположение исходных файлов, поэтому, изменение структуры проекта или перемещение исходных файлов в проекте может привести к тому, что конструктор классов не будет отслеживать тип, особенно исходный тип для typedef, базовые классы или типы ассоциаций. Может возникнуть ошибка, например **Конструктору классов не удалось отобразить этот тип**. В этом случае перетащите измененный или перемещенный исходный код в схему классов и повторно отобразите ее.  
  
Вы можете получить помощь по другим ошибкам и предупреждениям в следующих ресурсах:  
  
[Работа с кодом на Visual C++](working-with-visual-cpp-code.md)  
Содержит сведения об устранении неполадок при отображении C++ на схеме классов.  
  
[Форум по конструкторам классов Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
Форум предназначен для вопросов по работе с конструктором классов.  
  
## <a name="see-also"></a>См. также
[Разработка и просмотр классов и типов](designing-and-viewing-classes-and-types.md)