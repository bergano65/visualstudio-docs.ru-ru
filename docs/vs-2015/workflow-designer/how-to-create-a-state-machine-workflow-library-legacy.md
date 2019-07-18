---
title: Практическое руководство. Создать библиотеку рабочих процессов конечного автомата (для прежних версий) | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: acfa4a979614269c07969e4c01df4e994195cd64
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697120"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Практическое руководство. Создание библиотеки рабочих процессов конечного автомата (для прежних версий)
Выполните следующие шаги для создания проекта библиотеки рабочего процесса конечного автомата с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../includes/vs2010-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>Создание проекта библиотеки рабочего процесса конечного автомата.  
  
1. Запустите Visual Studio.  
  
2. В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
3. Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** параметр в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.  
  
    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.  
  
4. В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.  
  
5. В **шаблоны** области выберите **библиотеки рабочего процесса автомата**.  
  
6. В **имя** введите описательное имя для проекта, чтобы облегчить его определение.  
  
7. В **расположение** введите каталог, в котором вы хотите сохранить проект, или **Обзор** для перехода к нему.  
  
     Если необходимо создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.  
  
8. Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Рабочие процессы конечного автомата](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d)