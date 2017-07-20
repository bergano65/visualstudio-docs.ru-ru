---
title: "Практическое руководство. Создание и удаление зависимостей проекта | Документы Майкрософт"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: 896da11aa3bc92d153608dc09778817a77eaf7d6
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# Практическое руководство. Создание и удаление зависимостей проекта
<a id="how-to-create-and-remove-project-dependencies" class="xliff"></a>
При создании решения, содержащего несколько проектов, может потребоваться выполнить сначала сборку отдельных проектов для создания кода, используемого последующими проектами. Когда проект использует исполняемый код, создаваемый другим проектом, последний называется зависимостью первого. Такие отношения зависимости можно определить в диалоговом окне **Зависимости проектов**.  

### Назначение зависимостей проектам
<a id="to-assign-dependencies-to-projects" class="xliff"></a>  

1.  Выберите проект в Обозревателе решений.  

2.  В меню **Проект** выберите пункт **Зависимости проектов**.  

     Открывается диалоговое окно **Зависимости проектов**.  

    > [!NOTE]
    >  Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.  

3.  На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.  

4.  В поле **Зависит от** установите флажок для любого другого проекта, сборка которого должна быть выполнена раньше, чем сборка данного проекта.  

 Для создания зависимостей проектов решение должно состоять из нескольких проектов.  

### Удаление зависимостей проектов
<a id="to-remove-dependencies-from-projects" class="xliff"></a>  

1.  Выберите проект в Обозревателе решений.  

2.  В меню **Проект** выберите пункт **Зависимости проектов**.  

     Открывается диалоговое окно **Зависимости проектов**.  

    > [!NOTE]
    >  Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.  

3.  На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.  

4.  В поле **Зависит от** снимите флажки для тех проектов, которые более не являются зависимостями данного проекта.  

## См. также
<a id="see-also" class="xliff"></a>  
 [Building and Cleaning Projects and Solutions in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)  (Построение и очистка проектов и решений в Visual Studio)  
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)   
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Управление свойствами проектов и решений](managing-project-and-solution-properties.md)


