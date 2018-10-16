---
title: Дополнительные сведения об ошибках конструктора классов | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a957630de193d805b1a516d45c72bd1483f0278
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188530"
---
# <a name="additional-information-about-class-designer-errors"></a>Дополнительные сведения об ошибках конструктора классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструктор классов не отслеживает расположение исходных файлов, поэтому, изменение структуры проекта или перемещение исходных файлов в проекте может привести к тому, что конструктор классов не будет отслеживать тип, особенно исходный тип для typedef, базовые классы или типы ассоциаций. Может возникнуть ошибка, например **Конструктору классов не удалось отобразить этот тип**. В этом случае перетащите измененный или перемещенный исходный код в схему классов и повторно отобразите ее.  
  
 Вы можете получить помощь по другим ошибкам и предупреждениям в следующих ресурсах:  
  
 [Работа с кодом Visual C++ (конструктор классов)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Содержит сведения об устранении неполадок при отображении C++ на схеме классов.  
  
 [Форум по конструкторам классов Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
 Форум предназначен для вопросов по работе с конструктором классов.  
  
## <a name="see-also"></a>См. также  
 [Разработка и просмотр классов и типов](../ide/designing-and-viewing-classes-and-types.md)



