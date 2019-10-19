---
title: Руководство. Создание консольных приложений последовательного рабочего процесса (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662730"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Как создавать консольные приложения последовательных рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта консольного приложения последовательного рабочего процесса с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Создание консольного приложения последовательного рабочего процесса

1. Запустите Visual Studio.

2. В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. На панели **типы проектов** выберите визуальные C# проекты или проекты Visual Basic (в разделе **другие языки**), а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите **последовательное консольное приложение рабочего процесса**.

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к нему.

     Откроется конструктор Windows Forms и отобразится форма Form1 созданного проекта.

8. Нажмите кнопку **ОК**.

     Откроется конструктор рабочих процессов и отобразится рабочая область конструктора рабочих процессов созданного последовательного рабочего процесса.

9. Перетащите действие из области **элементов** в область конструктора в области **перетаскивания** назначенного действия.

## <a name="see-also"></a>См. также раздел
 [Создание проектов рабочих процессов прежних версий](../workflow-designer/creating-legacy-workflow-projects.md) [Разработка рабочих процессов](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)