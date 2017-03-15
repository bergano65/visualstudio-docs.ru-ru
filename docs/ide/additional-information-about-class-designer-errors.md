---
title: "Additional Information About Class Designer Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound"
  - "vs.classdesigner.CPlusPlusNoTypeFound"
  - "vs.classdesigner.CannotShowBaseType"
  - "vs.classdesigner.MatchOrphanTypesAtLoad"
  - "vs.classdesigner.CannotShowType"
  - "vs.classdesigner.AssociationTypeNotFoundError"
  - "vs.classdesigner.ViewInDiagramNoTypesFound"
  - "vs.classdesigner.CannotImplementInterface"
  - "vs.classdesigner.CannotShowImplementedInterface"
  - "vs.classdesigner.ViewInDiagramUnparsableTypeFound"
  - "vs.classdesigner.AssociationTypeNotFound"
  - "vs.classdesigner.CPlusPlusTypeCannotBeAdded"
helpviewer_keywords: 
  - "errors, class diagrams"
  - "errors, Class Designer"
  - "error messages, Class Designer"
  - "Class Designer [Visual Studio], errors"
  - "error messages, class diagrams"
  - "class diagrams, errors"
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Additional Information About Class Designer Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Конструктор классов не отслеживает расположение исходных файлов, поэтому, изменение структуры проекта или перемещение исходных файлов в проекте может привести к тому, что конструктор классов не будет отслеживать тип, особенно исходный тип для typedef, базовые классы или типы ассоциаций.  Может возникнуть ошибка, например **Class Designer is unable to display this type**.  В этом случае перетащите измененный или перемещенный исходный код в схему классов и повторно отобразите ее.  
  
 Вы можете получить помощь по другим ошибкам и предупреждениям в следующих ресурсах:  
  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Содержит сведения об устранении неполадок при отображении C\+\+ на схеме классов.  
  
 [Форум по конструктору классов Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
 Форум предназначен для вопросов по работе с конструктором классов.  
  
## См. также  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)