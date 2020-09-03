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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1403beccdb6bf9b938787f62cb3da2e5bb5c259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668123"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Практическое руководство. Создание и удаление зависимостей проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании решения, содержащего несколько проектов, может потребоваться выполнить сначала сборку отдельных проектов для создания кода, используемого последующими проектами. Когда проект использует исполняемый код, создаваемый другим проектом, последний называется зависимостью первого. Такие связи зависимостей можно определить в диалоговом окне **зависимости проекта** .

### <a name="to-assign-dependencies-to-projects"></a>Назначение зависимостей проектам

1. В обозревателе решений выберите проект.

2. В меню **Проект** выберите пункт **Зависимости проектов**.

    Открывается диалоговое окно **Зависимости проектов**.

   > [!NOTE]
   > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.

3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.

4. В поле **Зависит от** установите флажок для любого другого проекта, сборка которого должна быть выполнена раньше, чем сборка данного проекта.

   Для создания зависимостей проектов решение должно состоять из нескольких проектов.

### <a name="to-remove-dependencies-from-projects"></a>Удаление зависимостей проектов

1. В обозревателе решений выберите проект.

2. В меню **Проект** выберите пункт **Зависимости проектов**.

     Открывается диалоговое окно **Зависимости проектов**.

    > [!NOTE]
    > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.

3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.

4. В поле **Зависит от** снимите флажки для тех проектов, которые более не являются зависимостями данного проекта.

## <a name="see-also"></a>См. также:
 [Создание и очистка проектов и решений в Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Компиляция и построение](../ide/compiling-and-building-in-visual-studio.md) [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md) [NIB. изменение свойств проекта и параметров конфигурации](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
