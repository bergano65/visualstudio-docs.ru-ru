---
title: Как выполнить  настройку целевых платформ в проектах
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee7c0ee30ebe5a424439aab8e06c18c10fc679bf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942119"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Как выполнить  настройку целевых платформ в проектах

Visual Studio позволяет настраивать приложения для различных платформ, включая 64-разрядные платформы. Дополнительные сведения о поддержке 64-разрядных платформ в Visual Studio см. в статье [64-разрядные приложения](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Нацеливание на платформы с помощью диспетчера конфигураций

**Диспетчер конфигураций** позволяет быстро добавить новую платформу для нацеливания проекта. Если выбрать одну из платформ, входящих в Visual Studio, свойства проекта изменяются для сборки проекта в соответствии с выбранной платформой.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Настройка проекта для 64-разрядной платформы

1.  В строке меню последовательно выберите пункты **Сборка** > **Диспетчер конфигураций**.

2.  В списке **Активная платформа решения** выберите 64-разрядную платформу для нацеливания решения, а затем нажмите кнопку **Закрыть**.

    1.  Если нужная платформа не отображается в списке **Активная платформа решения**, выберите **Создать**.

         Откроется диалоговое окно **Создание платформы решения**.

    2.  В списке **Введите или выберите новую платформу** выберите **x64**.

        > [!NOTE]
        >  Если вы присваиваете конфигурации новое имя, может потребоваться изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

    3.  Если требуется скопировать параметры из текущий конфигурации платформы, выберите ее и нажмите кнопку **ОК**.

Обновляются свойства для всех проектов, нацеленных на 64-разрядную платформу, и следующая сборка проекта будет оптимизирована под 64-разрядные платформы.

## <a name="target-platforms-in-the-project-designer"></a>Нацеливание на платформы в конструкторе проектов

**Конструктор проектов** также предоставляет способ нацеливания проекта на различные платформы. Если выбор одной из платформ в списке диалогового окна **Создание платформы решения** не подходит для вашего решения, можно создать пользовательское имя конфигурации и изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

Способ выполнения этой задачи зависит от используемого языка программирования. Дополнительные сведения см. на следующих страницах:

- Для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] см. раздел [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Для проектов [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] см. статью [Страница "Сборка", конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Для проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] см. статью [/clr (компиляция CLR)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>См. также

- [Общие сведения о платформах построения](../ide/understanding-build-platforms.md)
- [/platform (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-разрядные приложения](/dotnet/framework/64-bit-apps)
- [Поддержка 64-разрядных сред IDE Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
