---
title: "Практическое руководство. Настройка проекта для конкретной платформы | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ccca87721c39daa7e613d7426c9d5fed6a144cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Практическое руководство. Настройка проекта для конкретной платформы
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет настраивать приложения для различных платформ, включая 64-разрядные платформы. Дополнительные сведения о поддержке 64-разрядных платформ в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в разделе [64-разрядные приложения](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Нацеливание на платформы с помощью диспетчера конфигураций  
 **Диспетчер конфигураций** позволяет быстро добавить новую платформу для нацеливания проекта. Если выбрать одну из платформ, входящих в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], свойства проекта изменяются под сборку проекта для выбранной платформы.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Настройка проекта для 64-разрядной платформы  
  
1.  В строке меню последовательно выберите пункты **Сборка**и **Диспетчер конфигураций**.  
  
2.  В списке **Активная платформа решения** выберите 64-разрядную платформу для нацеливания решения, а затем нажмите кнопку **Закрыть**.  
  
    1.  Если нужная платформа не отображается в списке **Активная платформа решения**, выберите **Создать**.  
  
         Откроется диалоговое окно **Создание платформы решения**.  
  
    2.  В списке **Введите или выберите новую платформу** выберите **x64**.  
  
        > [!NOTE]
        >  Если вы присваиваете конфигурации новое имя, может потребоваться изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.  
  
    3.  Если требуется скопировать параметры из текущий конфигурации платформы, выберите ее и нажмите кнопку **ОК**.  
  
 Обновляются свойства для всех проектов, нацеленных на 64-разрядную платформу, и следующая сборка проекта будет оптимизирована под 64-разрядные платформы.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Нацеливание на платформы в конструкторе проектов  
 Конструктор проектов также предоставляет способ нацеливания проекта на различные платформы. Если выбор одной из платформ в списке диалогового окна **Создание платформы решения** не подходит для вашего решения, можно создать пользовательское имя конфигурации и изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.  
  
 Способ выполнения этой задачи зависит от используемого языка программирования. Дополнительные сведения см. на следующих страницах:  
  
-   Для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] см. раздел [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Для проектов [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] см. раздел [Страница "Сборка", конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Для проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] см. раздел [/clr (компиляция CLR)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о платформах построения](../ide/understanding-build-platforms.md)   
 [/platform (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64-разрядные приложения](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Поддержка 64-разрядных сред IDE Visual Studio](../ide/visual-studio-ide-64-bit-support.md)