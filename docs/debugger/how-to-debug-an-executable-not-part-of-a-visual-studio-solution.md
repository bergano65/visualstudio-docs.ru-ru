---
title: Отладка приложения, которое не входит в состав решения Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557913"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Отладка приложения, которое не входит в решение Visual Studio (C++, C#, Visual Basic, F#)

Может потребоваться отладка приложения (*exe* -файла), которое не является частью решения Visual Studio. Это может быть проект [открытой папки](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) , или же вы или кто-то другой мог создать приложение за пределами Visual Studio или вы получили приложение в другом месте.

- Для проекта открытой папки в Visual Studio (не имеющего файла проекта или решения) см. раздел [Запуск и отладка кода](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) или, для C++, [Настройка параметров отладки с помощью Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Для приложения, которое не существует в Visual Studio, обычным способом отладки является запуск приложения за пределами Visual Studio, а затем присоединение к нему с помощью функции **присоединения к процессу** в отладчике Visual Studio. Дополнительные сведения см. [в разделе Присоединение к запущенным процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Для присоединения к приложению требуются ручные действия, которые могут занять несколько секунд. Из-за этой задержки подключение не поможет отладить проблемы при запуске или приложение, которое не ждет ввода данных пользователем и быстро завершается.

   В таких ситуациях можно создать проект Visual Studio EXE для приложения или импортировать его в существующее C#, Visual Basic или C++ решение. Не все языки программирования поддерживают исполняемые проекты.

>[!IMPORTANT]
>Функции отладки для приложения, не созданного в Visual Studio, ограничены, независимо от того, подключено ли приложение к приложению или добавлены в решение Visual Studio.
>
>Если у вас есть исходный код, лучшим подходом является импорт кода в проект Visual Studio. Затем запустите отладочную сборку приложения.
>
>Если у вас нет исходного кода и у приложения нет [отладочной информации](../debugger/how-to-set-debug-and-release-configurations.md) в совместимом формате, доступные функции отладки являются очень небольшими.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Создание нового EXE-проекта для существующего приложения

1. В Visual Studio выберите **файл** > **Открыть** > **проект**.

1. В диалоговом окне **Открытие проекта** выберите **все файлы проекта**, если они еще не выбраны, в раскрывающемся списке рядом с **именем файла**.

1. Перейдите в файл *exe* , выберите его и нажмите кнопку **Открыть**.

   Файл появится в новом временном решении Visual Studio.

1. Начните отладку приложения, выбрав команду выполнения, например **начать отладку**, в меню **Отладка** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Импорт приложения в существующее решение Visual Studio

1. Откройте решение C++, C#или Visual Basic в Visual Studio, выберите **файл** > **Добавить** > **существующий проект**.

1. В диалоговом окне **Открытие проекта** выберите **все файлы проекта**, если они еще не выбраны, в раскрывающемся списке рядом с **именем файла**.

1. Перейдите в файл *exe* , выберите его и нажмите кнопку **Открыть**.

   Файл отображается как новый проект в текущем решении.

1. После выбора нового файла запустите отладку приложения, выбрав команду выполнения, например **начать отладку**, в меню **Отладка** .

### <a name="see-also"></a>См. также:
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [DBG-файлы](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))