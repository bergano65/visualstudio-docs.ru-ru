---
title: Определение целевой версии .NET Framework в Visual Studio
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6d0eef8a9563fdb6d74737f90cf184186142a672
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Практическое руководство. Определение целевой версии .NET Framework

В этом документе описано, как выбрать целевую версию .NET Framework при создании проекта и как изменить целевую версию для существующего проекта Visual Basic, C# или Visual F#.

> [!IMPORTANT]
> Сведения об изменении целевой версии для проектов C++ см. в статье [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>Выбор целевой версии при создании проекта

При создании проекта доступные версии .NET Framework зависят от установленных версий и выбранного шаблона в диалоговом окне **Новый проект**.

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

1. В списке установленных шаблонов выберите тип проекта, который необходимо создать, и введите имя для проекта.

1. В раскрывающемся списке **Платформа** в верхней части диалогового окна **Новый проект** выберите версию .NET Framework, которая будет целевой для проекта.

    В списке платформ отображаются только те версии, которые можно применить к выбранному шаблону. Для некоторых типов проектов, например .NET Core, .NET Framework не требуется. В таких случаях раскрывающийся список **Платформа** скрывается.

    ![Раскрывающийся список Framework в диалоговом окне "Новый проект"](media/vside-newproject-framework.png)

1. Нажмите кнопку **ОК** .

## <a name="to-change-the-targeted-version"></a>Изменение целевой версии

Целевую версию .NET Framework в проекте Visual Basic, C# или Visual F# можно изменить, воспользовавшись следующей процедурой.

Сведения об изменении целевой версии для проектов C++ см. в статье [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.

    ![Свойства проводника Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

1. В левом столбце окна **Свойства** перейдите на вкладку **Приложение**.

    ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > После создания приложения UWP невозможно изменить целевую версию Windows или .NET Framework.

1. В списке **Целевая рабочая среда** выберите требуемую версию.

1. В открывшемся диалоговом окне проверки нажмите кнопку **Да**.

    Проект будет выгружен. При его перезагрузке он будет предназначен для выбранной версии .NET Framework.

    > [!NOTE]
    > Если код содержит ссылки на другую версию .NET Framework, отличную от целевой, при компиляции и запуске кода могут появиться сообщения об ошибках. Для устранения этих ошибок необходимо изменить ссылки. См. раздел [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>См. также

- [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)