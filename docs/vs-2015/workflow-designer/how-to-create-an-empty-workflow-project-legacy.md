---
title: Как создать пустой проект рабочего процесса (прежний) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d24baf48f74a7e18ee7bb4922ad989fd8e03a38a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662735"
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Как создать пустой проект рабочего процесса (для прежних версий)
Выполните следующие шаги для создания проекта пустого рабочего процесса с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-an-empty-workflow-project"></a>Создание пустого проекта рабочего процесса

1. Запустите Visual Studio.

2. В меню **Файл** последовательно выберите команды **Создать**и **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. На панели **типы проектов** выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите **пустой проект рабочего процесса**.

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к нему.

     Если требуется создать каталог решения для проекта, установите флажок **создать каталог для решения** и введите имя в поле **имя решения** .

8. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также:
 [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)