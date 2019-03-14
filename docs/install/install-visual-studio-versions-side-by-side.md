---
title: Параллельная установка версий Visual Studio
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-isntallation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b7b1eb1808fadf3bc7639662419f7d176909412c
ms.sourcegitcommit: e2b1932d3d4d77dfacb5d245c8b2c7490a94a20e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2019
ms.locfileid: "57683376"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Параллельная установка версий Visual Studio

Visual Studio можно установить на компьютер, на котором уже установлена более ранняя версия Visual Studio.

::: moniker range="vs-2017"

Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:

* При использовании Visual Studio 2017 для открытия решения, которое было создано в Visual Studio 2015, можно впоследствии снова открыть и изменить решение в более ранней версии, если в нем не реализованы никакие функции, относящиеся только к Visual Studio 2017.

* При попытке открыть решение, которое было создано в Visual Studio 2015 или более ранней версии, с помощью Visual Studio 2017 может потребоваться изменить проекты и файлы, чтобы они стали совместимы с Visual Studio 2017. Дополнительные сведения см. в разделе [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:

* При использовании Visual Studio 2019 для открытия решения, которое было создано в Visual Studio 2017, можно впоследствии снова открыть и изменить решение в более ранней версии, если в нем не реализованы никакие функции, относящиеся только к Visual Studio 2019.

* При попытке открыть решение, которое было создано в Visual Studio 2017 или более ранней версии, с помощью Visual Studio 2019 может потребоваться изменить проекты и файлы, чтобы они стали совместимы с Visual Studio 2019. Дополнительные сведения см. в разделе [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md).

::: moniker-end

* В случае удаления версии Visual Studio с компьютера, на котором установлено более одной версии, сопоставления файлов Visual Studio будут удалены для всех версий.

* Visual Studio не обновляет расширения автоматически, так как не все расширения совместимы. Необходимо переустановить расширения из [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) или с помощью средств издателя программного обеспечения.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Версии платформы .NET Framework и установка нескольких версий на один компьютер

В проектах Visual Basic, Visual C# и Visual F# параметр **Целевая рабочая среда** в **конструкторе проектов** используется для определения того, какая версия платформы .NET Framework используется в проекте. Для проекта C++ можно вручную изменить целевую платформу, изменив VCXPROJ-файл. Дополнительные сведения см. в разделе [Совместимость версий в .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

При создании проекта можно указать целевую версию .NET Framework проекта в списке **.NET Framework** в диалоговом окне **Создание проекта** .

Сведения, относящиеся к конкретному языку, см. в соответствующем разделе следующей таблицы.

::: moniker range="vs-2017"

| Язык | Раздел |
|--------------|-----------|
| Visual Basic | [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Разработка в Visual Studio с использованием Visual F#](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md?view=vs-2017)
* [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Создание изолированных приложений и параллельных сборок C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Язык | Раздел |
|--------------|-----------|
| Visual Basic | [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2019) |
| Visual C# | [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2019) |
| Visual F# | [Разработка в Visual Studio с использованием Visual F#](../ide/fsharp-visual-studio.md?view=vs-2019) |
| C++ | [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md?view=vs-2019)
* [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md)
* [Создание изолированных приложений и параллельных сборок C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end