---
title: "Как: Создание консольного приложения последовательного рабочего процесса (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e9732334f422b4042f2cd581afaea06bf99ab16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Как создавать консольные приложения последовательных рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта консольного приложения последовательного рабочего процесса с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Создание консольного приложения последовательного рабочего процесса  
  
1.  Запустите Visual Studio.  
  
2.  На **файл** последовательно выберите пункты **New**, а затем выберите **проекта**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.  
  
    > [!NOTE]
    >  Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.  
  
4.  В **типы проектов** области, выберите проекты Visual C# или проекты Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.  
  
5.  В **шаблоны** выберите **консольного приложения последовательного рабочего процесса**.  
  
6.  В **имя** введите описательное имя проекта облегчить его определение.  
  
7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.  
  
     Откроется конструктор Windows Forms и отобразится форма Form1 созданного проекта.  
  
8.  Нажмите кнопку **ОК**.  
  
     Откроется конструктор рабочих процессов и отобразится рабочая область конструктора рабочих процессов созданного последовательного рабочего процесса.  
  
9. Перетащите действие с **элементов** в область конструктора в **перетащите действие** назначенную область.  
  
## <a name="see-also"></a>См. также  
 [Создание проектов рабочих процессов прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Разработка рабочих процессов](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)