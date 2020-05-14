---
title: Устранение неполадок VSPackages (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698915"
---
# <a name="troubleshooting-vspackages"></a>Устранение неполадок, связанных с пакетами VSPackage
Ниже приведены общие проблемы, которые вы могли бы иметь с вашим VSPackage и советы по решению проблем.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Для устранения неполадок VSPackage, который удерживает Visual Studio от запуска

- Запуск [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме.

   Чтобы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] начать в безопасном режиме, по команде запрос, введите **devenv.exe /safemode**.

   Во время этого процесса никакие VSPackages не будут [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]нагружены за исключением VSPackages которые включены с .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Для устранения неполадок VSPackage, который не загружается

1. Убедитесь, что вы используете корень реестра, в котором VSPackage зарегистрирован для запуска, как правило, экспериментальный корень реестра.

    Для получения дополнительной информации [см.](../extensibility/the-experimental-instance.md)

2. Если VSPackage предназначен для запуска в экспериментальном корне реестра, убедитесь, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]что вы работаете экспериментальную версию.

    Чтобы запустить экспериментальную версию, введите следующее в командном окне: **devenv /rootsuffix exp.**

3. Проверьте свои записи в реестре VSPackage.

    Для получения дополнительной информации [Managing VSPackages](../extensibility/managing-vspackages.md)см. [Registering VSPackages](registering-and-unregistering-vspackages.md)

4. Открыть окно **вывода** экземпляра, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] что не в состоянии загрузить VSPackage. В этом окне может отображаться информация о том, почему VSPackage не загружается.

   > [!NOTE]
   > Если вы начинаете экспериментальную версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), проинспектировать окно **выхода** обеих версий.

5. Изучите журнал активности.

    Для получения дополнительной информации [см.](../extensibility/how-to-use-the-activity-log.md)

6. Для получения дополнительной информации об исключениях, брошенных IDE, нажмите **«Исключения»** в меню **Debug,** чтобы включить исключения. В диалоговом поле **Исключений** выберите типы исключений, о которых требуется дополнительная информация.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Для устранения неполадок VSPackage, который не регистрируется

1. Убедитесь, что сборка VSPackage находится в надежном месте. RegPkg не может регистрировать сборки в ненадежном или частично надежном месте, например, в сетевой доле в конфигурации безопасности .net по умолчанию. Хотя предупреждение появляется всякий раз, когда пользователь создает проект в ненадежном месте, флажок "не показывать это сообщение" может предотвратить повторение этого предупреждения.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Устранение неполадок команды, которая не видна или генерирует ошибку при нажатии на команду

1. Слияние новых или измененных команд меню и тех, которые уже [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в IDE, введя следующее в командный запрос: **devenv /rootsuffix Exp /setup**.

2. Убедитесь, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] что можно найти UI.dll для вашего VSPackage.

   1. Найти CLSID VSPackage в разделе Пакеты реестра:

        HKLM-Программное обеспечение,Microsoft-Визуальная версия студии\\*\<>*«Пакеты

   2. Убедитесь, что путь, данный подключку SatelliteDll, является правильным.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Для устранения неполадок VSPackage, который ведет себя неожиданно

1. Задайте точки останова в коде.

     Хорошими отправной точкой для отладки являются конструктор и метод инициализации. Вы также можете установить точки разрыва в области, которые вы хотите оценить, например, команду меню. Для включения моментов разрыва необходимо работать под отладчиком.

    1. В меню **Проект** выберите **Свойства**.

    2. На диалоговом поле **Страницы свойств** выберите вкладку **Debug.**

    3. В поле **аргументов командной строки** введите исходный суффикс среды разработки, на который нацелен ваш VSPackage. Например, чтобы выбрать экспериментальную сборку, введите: **/RootSuffix Exp**.

    4. В меню **Debug** щелкните **Start Debugging** или нажмите F5.

        > [!NOTE]
        > Если вы отлажаете проект, создайте или загрузите существующий экземпляр проекта сейчас.

2. Используйте журнал активности.

     Отслеживай поведение VSPackage, записывая информацию в журнал активности в ключевых точках. Этот метод особенно полезен при запуске VSPackage в розничной среде. Для получения дополнительной информации [см.](../extensibility/how-to-use-the-activity-log.md)

3. Используйте общедоступные символы.

     Чтобы улучшить читаемость во время отладки, можно прикрепить символы к отладчику.

    1. Из меню **«Инструменты/Опции»** перейдите в диалоговую **будку «Отладка/символы».**

    2. Добавьте это **местоположение файла символа (.pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Чтобы повысить производительность, укажите папку кэша символов, например:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Для устранения неполадок отсутствующих VSPackage или одной из его зависимостей

1. Для управляемого кода убедитесь, что ссылки являются правильными.

   1. В меню **Проект** выберите **Свойства**.

   2. Выберите вкладку **Ссылки** в диалоговом поле **Страниц ы свойств** и убедитесь, что все пути верны. Кроме того, можно использовать **браузер объектов** для просмотра упомянутых объектов.

        Для управляемого кода можно использовать [Fuslogvw.exe (Ассамблея Связывающий блог Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) для отображения деталей неудавшихся сборочных нагрузок.

2. Для неуправляемого кода найдите CLSID VSPackage в узлу реестра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID:

    HKLM-Программное обеспечение,Microsoft-Визуальная версия Studio\\*\<>*»CLSID

   Убедитесь, что запись InprocServer32 имеет правильный путь VSPackage dll.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
