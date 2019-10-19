---
title: Как создать консольные приложения для рабочего процесса конечного автомата (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48c7e06c2cb0e59de754b1ab36b693c4c9872985
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662719"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Как создать консольные приложения рабочих процессов конечных автоматов (для прежних версий)
Выполните следующие шаги для создания проекта консольного приложения рабочего процесса конечного автомата с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-application-project"></a>Создание проекта приложения конечного автомата

1. Запустите Visual Studio.

2. В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. На панели **типы проектов** выберите визуальный C# элемент или Visual Basic (в разделе **другие языки**), а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите **консольное приложение рабочего процесса конечного автомата**.

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к нему.

     Если требуется создать каталог решения для проекта, установите флажок **создать каталог для решения** и введите имя в поле **имя решения** .

8. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел
 [Создание устаревших проектов рабочих процессов](../workflow-designer/creating-legacy-workflow-projects.md) [руководство. Создание библиотеки рабочих процессов конечного автомата (устаревшая)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)