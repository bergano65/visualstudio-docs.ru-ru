---
title: Целевая версия .NET
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747124"
---
# <a name="how-to-target-a-version-of-net"></a>Практическое руководство. Определение целевой версии .NET

Эта статья описывает определение конкретной целевой версии платформы .NET Framework при создании проекта .NET Framework. Кроме того, она описывает, как изменить целевую версию для существующего проекта Visual Basic, C# или F#.

> [!IMPORTANT]
> Дополнительные сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Выбор целевой версии при создании проекта

При создании проекта .NET Framework доступные версии .NET Framework зависят от установленных версий и выбранного шаблона проекта.

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

1. Выберите шаблон .NET Framework для типа проекта, который требуется создать.

1. В раскрывающемся списке **Платформа** в нижней части диалогового окна выберите целевую версию .NET Framework для проекта.

   В списке платформ отображаются только те версии, которые можно применить к выбранному шаблону.

   > [!NOTE]
   > Для некоторых типов проектов, например .NET Core, раскрывающийся список **Платформа** не отображается.

   ::: moniker range="vs-2017"

   ![Раскрывающийся список "Платформа" в диалоговом окне "Новый проект" Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Средство выбора платформы в Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Продолжайте [создание проекта](create-new-project.md).

## <a name="change-the-targeted-version"></a>Изменение целевой версии

Целевую версию .NET в проекте Visual Basic, C# или F# можно изменить, воспользовавшись указанной ниже процедурой.

1. В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.

    ![Свойства проводника Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. В левом столбце окна **Свойства** перейдите на вкладку **Приложение**.

    ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > После создания приложения UWP невозможно изменить целевую версию Windows или .NET.

1. В списке **Целевая рабочая среда** выберите требуемую версию.

1. В открывшемся диалоговом окне проверки нажмите кнопку **Да**.

    Проект будет выгружен. При его перезагрузке он будет ориентирован на выбранную версию .NET.

    > [!NOTE]
    > Если код содержит ссылки на другую версию .NET, отличную от целевой, при компиляции и запуске кода могут появиться сообщения об ошибках. Для устранения этих ошибок необходимо изменить ссылки. См. раздел [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>См. также

- [Общие сведения о настройке для платформы](../ide/visual-studio-multi-targeting-overview.md)
- [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)