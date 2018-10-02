---
title: 'Практическое: Создание консольного приложения последовательного рабочего процесса (для прежних версий) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0882a39dfae5639fcfc72adc7ccd976f4d93e30a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563704"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Как создавать консольные приложения последовательных рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта консольного приложения последовательного рабочего процесса с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Создание консольного приложения последовательного рабочего процесса  
  
1.  Запустите Visual Studio.  
  
2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** параметр в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.  
  
    > [!NOTE]
    >  Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.  
  
4.  В **типы проектов** области, выберите проекты Visual C# или проекты Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.  
  
5.  В **шаблоны** области выберите **консольного приложения последовательного рабочего процесса**.  
  
6.  В **имя** введите описательное имя для проекта, чтобы облегчить его определение.  
  
7.  В **расположение** введите каталог, в котором вы хотите сохранить проект, или **Обзор** для перехода к нему.  
  
     Откроется конструктор Windows Forms и отобразится форма Form1 созданного проекта.  
  
8.  Нажмите кнопку **ОК**.  
  
     Откроется конструктор рабочих процессов и отобразится рабочая область конструктора рабочих процессов созданного последовательного рабочего процесса.  
  
9. Перетащите действие из **элементов** в область конструктора в **перетащите действие** назначенную область.  
  
## <a name="see-also"></a>См. также  
 [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Разработка рабочих процессов](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)