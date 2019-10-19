---
title: Практическое руководство. Настройка проекта для конкретной платформы | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668194"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Практическое руководство. Настройка проекта для конкретной платформы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет настраивать приложения для различных платформ, включая 64-разрядные платформы. Дополнительные сведения о поддержке 64-разрядных платформ в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] см. в разделе [64-разрядные приложения](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Нацеливание на платформы с помощью диспетчера конфигураций
 **Диспетчер конфигураций** позволяет быстро добавить новую платформу для нацеливания проекта. Если выбрать одну из платформ, входящих в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], свойства проекта изменяются под сборку проекта для выбранной платформы.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Настройка проекта для 64-разрядной платформы

1. В строке меню последовательно выберите пункты **Сборка**и **Диспетчер конфигураций**.

2. В списке **Активная платформа решения** выберите 64-разрядную платформу для нацеливания решения, а затем нажмите кнопку **Закрыть**.

   1. Если нужная платформа не отображается в списке **Активная платформа решения**, выберите **Создать**.

        Откроется диалоговое окно **Создание платформы решения**.

   2. В списке **Введите или выберите новую платформу** выберите **x64**.

       > [!NOTE]
       > Если вы присваиваете конфигурации новое имя, может потребоваться изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

   3. Если требуется скопировать параметры из текущий конфигурации платформы, выберите ее и нажмите кнопку **ОК**.

   Обновляются свойства для всех проектов, нацеленных на 64-разрядную платформу, и следующая сборка проекта будет оптимизирована под 64-разрядные платформы.

## <a name="targeting-platforms-in-the-project-designer"></a>Нацеливание на платформы в конструкторе проектов
 Конструктор проектов также предоставляет способ нацеливания проекта на различные платформы. Если выбор одной из платформ в списке диалогового окна **Создание платформы решения** не подходит для вашего решения, можно создать пользовательское имя конфигурации и изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

 Способ выполнения этой задачи зависит от используемого языка программирования. Дополнительные сведения см. на следующих страницах:

- Для проектов [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] см. раздел [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- Для проектов [!INCLUDE[csprcs](../includes/csprcs-md.md)] см. раздел [Страница "Сборка", конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Для проектов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] см. раздел [/clr (компиляция CLR)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>См. также
 [Общие сведения о платформах сборки](../ide/understanding-build-platforms.md) [/Platform (C# параметры компилятора)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64-разрядные приложения](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Поддержка Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)
