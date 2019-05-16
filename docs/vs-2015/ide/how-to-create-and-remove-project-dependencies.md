---
title: Практическое руководство. Создание и удаление зависимостей проекта | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e4b039f514c7d43e768becca8532a05fb14785b3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680366"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Практическое руководство. Создание и удаление зависимостей проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании решения, содержащего несколько проектов, может потребоваться выполнить сначала сборку отдельных проектов для создания кода, используемого последующими проектами. Когда проект использует исполняемый код, создаваемый другим проектом, последний называется зависимостью первого. Такие отношения зависимости можно определить в диалоговом окне **Зависимости проектов**.  
  
### <a name="to-assign-dependencies-to-projects"></a>Назначение зависимостей проектам  
  
1. Выберите проект в Обозревателе решений.  
  
2. В меню **Проект** выберите пункт **Зависимости проектов**.  
  
    Открывается диалоговое окно **Зависимости проектов**.  
  
   > [!NOTE]
   > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.  
  
3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.  
  
4. В поле **Зависит от** установите флажок для любого другого проекта, сборка которого должна быть выполнена раньше, чем сборка данного проекта.  
  
   Для создания зависимостей проектов решение должно состоять из нескольких проектов.  
  
### <a name="to-remove-dependencies-from-projects"></a>Удаление зависимостей проектов  
  
1. Выберите проект в Обозревателе решений.  
  
2. В меню **Проект** выберите пункт **Зависимости проектов**.  
  
     Открывается диалоговое окно **Зависимости проектов**.  
  
    > [!NOTE]
    > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.  
  
3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.  
  
4. В поле **Зависит от** снимите флажки для тех проектов, которые более не являются зависимостями данного проекта.  
  
## <a name="see-also"></a>См. также раздел  
 [Building and Cleaning Projects and Solutions in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)  (Построение и очистка проектов и решений в Visual Studio)  
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)   
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [NIB. Практическое руководство. Изменение свойств проекта и параметров конфигурации](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
