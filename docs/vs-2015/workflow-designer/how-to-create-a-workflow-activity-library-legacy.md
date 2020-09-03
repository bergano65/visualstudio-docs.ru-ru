---
title: Как создать библиотеку действий рабочего процесса (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604964"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Как создать библиотеку действий рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта библиотеки действий рабочего процесса с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Создание проекта библиотеки действий рабочих процессов

1. Запустите Visual Studio.

2. В меню **Файл** последовательно выберите команды **Создать**и **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. На панели **типы проектов** выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите **Библиотека действий рабочего процесса**.

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к нему.

     Если требуется создать каталог решения для проекта, установите флажок **создать каталог для решения** и введите имя в поле **имя решения** .

8. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также:
 [Создание устаревших проектов рабочих процессов](../workflow-designer/creating-legacy-workflow-projects.md) с помощью устаревших [действий рабочего процесса](../workflow-designer/legacy-workflow-activities.md) [в конструкторе](../workflow-designer/using-the-legacy-activity-designer.md) устаревшие действия [Разработка действий рабочего процесса](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) [Windows Workflow Foundation действия](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)