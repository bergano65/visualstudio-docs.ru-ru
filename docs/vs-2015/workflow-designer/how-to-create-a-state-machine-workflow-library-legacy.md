---
title: Как создать библиотеку рабочих процессов конечного автомата (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663377"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Как создать библиотеку рабочих процессов конечного автомата (для прежних версий)
Выполните следующие шаги для создания проекта библиотеки рабочего процесса конечного автомата с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Создание проекта библиотеки рабочего процесса конечного автомата.

1. Запустите Visual Studio.

2. В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. На панели **типы проектов** выберите визуальный C# элемент или Visual Basic (в разделе **другие языки**), а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите **Библиотека рабочих процессов конечного автомата**.

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к нему.

     Если требуется создать каталог решения для проекта, установите флажок **создать каталог для решения** и введите имя в поле **имя решения** .

8. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел
 Создание [рабочих процессов конечного автомата](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d) для [проектов рабочих процессов прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)