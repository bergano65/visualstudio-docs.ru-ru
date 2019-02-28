---
title: Подготовка к отладке приложений Windows Forms | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cc06e33b3549bda9bdc9fe04073ca4cf0d9e9a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679952"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Подготовка к отладке: приложения Windows Forms
Шаблон проекта Windows Forms создает приложение Windows Forms. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений. Дополнительные сведения см. в разделе [Создание проекта приложения Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости эти параметры можно изменить. Эти параметры могут быть изменены в диалоговом окне **Страницы свойств \<имя проекта>** (**Мой проект** в Visual Basic).

 Дополнительные сведения см. в разделе [рекомендуемые параметры свойств](../debugger/managed-debugging-recommended-property-settings.md).

 В следующей таблице приведены дополнительные параметры, рекомендуемые к использованию.

### <a name="configuration-properties-in-debug-tab"></a>"Свойства конфигурации" во вкладке "Отладка"

|**Имя свойства**|**Параметр**|
|-----------------------|-----------------|
|**Действие при запуске**|— Установите **Запуск проекта** в большинстве случаев. Установите **Запуск внешней программы**, если требуется запускать другой исполняемый файл при запуске отладки (обычно для отладки DLL).|

 Можно выполнять отладку приложений Windows Forms из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или путем присоединения к уже запущенному приложению. Дополнительные сведения о присоединении см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Выполнение отладки приложения Windows Forms на C#, F# или Visual Basic

1. Откройте проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Создайте точки останова, если требуется.

    Поскольку приложения Windows Forms управляются событиями, точки останова появятся в коде обработчиков событий, или в методах, вызываемых ими. Типичные события, в которые стоит помещать точки останова:

   1. события, связанные с элементом управления, такие как Click, Enter, и т.д.;

   2. события, связанные с запуском приложений и завершением работы, такие как Load, Activated и т. д.;

   3. события, связанные с фокусом и проверками.

      Подробнее см. в разделе [Создание обработчиков событий в Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. В меню **Отладка** выберите команду **Запуск**.

4. Отладка использует методы, обсуждаемые в [сначала посмотрим, отладчик](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>См. также раздел
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Практическое руководство. Настройка конфигураций отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)
- [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)