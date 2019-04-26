---
title: Целевая версия .NET Framework.
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548664"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Как выполнить Определение целевой версии .NET Framework

Эта статья описывает определение целевой версии платформы .NET Framework при создании проекта. Кроме того, она описывает, как изменить целевую версию для существующего проекта Visual Basic, C# или F#.

> [!IMPORTANT]
> Дополнительные сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Выбор целевой версии при создании проекта

При создании проекта доступные версии .NET Framework зависят от установленных версий и выбранного шаблона проекта.

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

1. Выберите шаблон для типа проекта, который требуется создать. Введите имя проекта.

1. В раскрывающемся списке **Платформа** в нижней части диалогового окна выберите целевую версию .NET Framework для проекта.

   В списке платформ отображаются только те версии, которые можно применить к выбранному шаблону. Для некоторых типов проектов, например .NET Core, .NET Framework не требуется. В таких случаях раскрывающийся список **Платформа** скрывается.

   ::: moniker range="vs-2017"

   ![Раскрывающийся список Framework в диалоговом окне "Новый проект"](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Средство выбора платформы в Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Продолжайте [создание проекта](create-new-project.md).

## <a name="change-the-targeted-version"></a>Изменение целевой версии

Целевую версию .NET Framework в проекте Visual Basic, C# или F# можно изменить, воспользовавшись указанной ниже процедурой.

1. В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.

    ![Свойства проводника Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. В левом столбце окна **Свойства** перейдите на вкладку **Приложение**.

    ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

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