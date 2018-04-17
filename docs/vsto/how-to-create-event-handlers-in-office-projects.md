---
title: 'Как: Создание обработчиков событий в проектах Office | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Практическое руководство. Создание обработчиков событий в проектах Office
  Существует несколько способов создания обработчиков событий в Visual Basic и C#. В режиме конструктора можно создать обработчики событий для элементов управления по умолчанию, дважды щелкнув элемент управления или используйте панель события **свойства** окно для создания обработчиков событий в элементе управления. Однако при работе в представлении кода не можно переключиться в режим конструктора, чтобы создать обработчик событий.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Чтобы создать обработчик событий в Visual Basic  
  
1.  Из **имя класса** раскрывающемся списке в верхней части редактора кода, выберите объект, который вы хотите создать обработчик событий.  
  
    > [!NOTE]  
    >  Если вы хотите создавать обработчики событий для `ThisDocument` или `ThisWorkbook`, необходимо выбрать **(события ThisDocument)** или **(события ThisWorkbook)** в **имя класса**раскрывающегося списка  
  
2.  Из **имя метода** раскрывающегося списка в верхней части редактора кода, выберите событие.  
  
     Visual Studio создает обработчик событий и перемещает курсор на вновь созданный обработчик событий. Если обработчик событий уже существует, курсор перемещается в существующий обработчик событий.  
  
### <a name="to-create-an-event-handler-in-c"></a>Чтобы создать обработчик событий в C#  
  
1.  Создайте делегат события в **запуска** событие класса, введя имя события, пробел и введя **+=** без пробелов после него. Пример:  
  
     `this.<object name>.<event name> +=`  
  
2.  В конце строки кода дважды нажмите клавишу TAB.  
  
     Visual Studio автоматически завершает строку кода, будет создан обработчик событий и перемещает курсор на вновь созданный обработчик событий.  
  
## <a name="see-also"></a>См. также  
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Пошаговое руководство: Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)  
  
  