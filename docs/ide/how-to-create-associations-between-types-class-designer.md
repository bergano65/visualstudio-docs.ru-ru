---
title: "How to: Create Associations Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.associationline"
helpviewer_keywords: 
  - "types [Visual Studio], associations"
  - "association lines, defining (Class Designer)"
  - "defining association lines (Class Designer)"
  - "associations, types"
  - "association lines"
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create Associations Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Линии связи в конструкторе классов показывают отношения между классами в схеме.  Линия связи представляет класс, который является типом "свойство" или "поле" другого класса в проекте.  Линии связи обычно используются для иллюстрации наиболее важных отношений между классами в проекте.  
  
 Можно отобразить все поля и свойства как ассоциации, но более рационально отображать как ассоциации только самые важные члены, в зависимости от того, что требуется акцентировать на схеме. \(Менее важные члены можно отобразить как обычные члены или скрыть их совсем.\)  
  
> [!NOTE]
>  Конструктор классов поддерживает только однонаправленные ассоциации.  
  
### Определение линии связи в конструкторе классов  
  
1.  В области инструментов, в разделе "Конструктор классов" щелкните элемент **Связь**.  
  
2.  Нарисуйте линию между двумя фигурами, которые необходимо связать ассоциацией.  
  
     В первом классе будет создано новое свойство.  Данное свойство отображается как линия связи \(не как свойство в секции фигуры\) с именем по умолчанию.  Его тип является фигурой, на которую указывает линия связи.  
  
### Изменение имени ассоциации  
  
-   На рабочей области конструирования щелкните метку линии связи и введите новое имя.  
  
 — либо —  
  
1.  Щелкните фигуру, которая содержит свойство, отображаемое как ассоциация.  
  
     Фигура получит фокус, и ее члены отобразятся в окне "Сведения о классе" и в окне "Свойства".  
  
2.  В окне "Сведения о классе" или в окне "Свойства" введите имя поля для свойства и нажмите клавишу ВВОД.  
  
     Имя обновится в окне **Сведения о классе**, на линии связи, в окне "Свойства" и в коде.  
  
## См. также  
 [How to: Change Between Member Notation and Association Notation \(Class Designer\)](../Topic/How%20to:%20Change%20Between%20Member%20Notation%20and%20Association%20Notation%20\(Class%20Designer\).md)