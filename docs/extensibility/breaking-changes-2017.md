---
title: Нарушение изменений в визуальной студии 2017 расширяемость
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739974"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Изменения в визуальной студии 2017 расширяемость

Visual Studio 2017 обеспечивает [более быстрый и легкий опыт установки Visual Studio,](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) который снижает влияние Visual Studio на пользовательские системы, предоставляя пользователям больший выбор над рабочими нагрузками и функциями, которые установлены. Чтобы поддержать эти улучшения, мы внесли изменения в модель расширяемости, включая некоторые изменения. В этой статье описаны технические детали этих изменений и что можно сделать для их устранения.

> [!NOTE]
> Некоторая информация — это детали реализации point-in-time, и она может быть изменена позже.

## <a name="changes-affecting-vsix-format-and-installation"></a>Изменения, влияющие на формат и установку VSIX

Visual Studio 2017 представила формат VSIX v3 (версия 3) для поддержки легкой установки.

Изменения в формате VSIX включают:

* Декларация предпосылок для установки. Чтобы выполнить обещание легкой, быстро устанавливаемых Visual Studio, установщик теперь предлагает больше вариантов конфигурации для пользователей. В результате, чтобы гарантировать, что функции и компоненты, необходимые для расширения установлены, расширения должны объявить свои зависимости.

  * Установщик Visual Studio 2017 автоматически предлагает приобрести и установить необходимые компоненты для пользователя в рамках установки расширения.
  * Пользователи также предупреждают при попытке установить расширение, которое не было построено с использованием нового формата VSIX v3, даже если они были отмечены в их манифесте как целевая версия 15.0.

* Расширенные возможности для формата VSIX. Чтобы обеспечить [низкоэффективное установку](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) Visual Studio, которая также поддерживает установки бок о бок, мы больше не сохраняем большинство данных конфигурации в системном реестре и перемещаем сборки Visual Studio из GAC. Мы также увеличили возможности формата VSIX и установки VSIX, что позволило вам использовать его, а не MSI или EXE для установки расширений для некоторых типов установки.

Новые возможности включают в себя:

* Регистрация в указанном экземпляре Visual Studio.
* Установка вне [папки расширений.](set-install-root.md)
* Обнаружение архитектуры процессоров.
* Зависимость от языковых пакетов.
* Установка с [поддержкой NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Построить расширение для Visual Studio 2017

Дизайнерский инструмент для автором нового формата VSIX v3 доступен в Visual Studio 2017. Смотрите сопроводительный документ [Как: Миграция расширения проектов Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) для получения подробной информации об использовании инструментов дизайнера или ручного обновления проекта и манифест для разработки VSIX v3 расширений.

## <a name="change-visual-studio-user-data-path"></a>Изменение: Путь данных пользователей Visual Studio

Ранее на каждой машине могла существовать только одна установка каждого крупного релиза Visual Studio. Для поддержки бок о бок установки Visual Studio 2017, несколько пользовательских путей данных для Visual Studio может существовать на машине пользователя.

Код, работающий внутри процесса Visual Studio, должен быть обновлен, чтобы использовать visual Studio Settings Manager. Код, работающий за пределами процесса Visual Studio, может найти путь пользователя для конкретной установки Visual Studio, [следуя инструкциям здесь.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>Изменение: Кэш Глобальной Ассамблеи (GAC)

Большинство ядре Visual Studio больше не устанавливаются в GAC. Следующие изменения были внесены таким образом, чтобы код, работающий в процессе Visual Studio, мог по-прежнему находить необходимые сборки во время выполнения.

> [!NOTE]
> «INSTALLDIR» ниже ссылается на корневой каталог установки Visual Studio. *VSIXInstaller.exe* автоматически заселит это, но для записи пользовательского кода развертывания, пожалуйста, прочитайте [расположение Visual Studio](locating-visual-studio.md).

* Собрания, которые были установлены только в GAC:

  Эти сборки в настоящее время установлены в соответствии с <em>«INSTALLDIR»(Common7»IDE\*, «INSTALLDIR»»Common7»IDE-PublicAssemblies</em> или *«INSTALLDIR»-Common7»IDE-PrivateAssemblies*. Эти папки являются частью прощупывающих путей процесса Visual Studio.

* Сборки, которые были установлены в незондирующий путь и в GAC:

  * Копия в GAC была удалена из установки.
  * Файл *.pkgdef* был добавлен для указания базовой записи кода для сборки.

    Пример:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    В течение выполнения подсистема Visual Studio pkgdef объединяет эти записи в файл конфигурации времени выполнения visual Studio (под [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) элементами *«VSAPPDATA».devenv.exe.config).* Это рекомендуемый способ, чтобы позволить visual Studio процесс найти сборку, потому что он избегает поиска через зондирования путей.

### <a name="reacting-to-this-breaking-change"></a>Реагирование на это нарушение изменения

* Если расширение работает в процессе Visual Studio:

  * Ваш код сможет найти основные сборки Visual Studio.
  * Рассмотрите возможность использования файла *.pkgdef* для указания пути к сборкам, если это необходимо.

* Если расширение работает вне процесса Visual Studio:

  Рассмотрите возможность поиска основных сборок Visual Studio в соответствии с <em>«INSTALLDIR»»Common7»IDE,\*«INSTALLDIR» («Common7») PublicAssemblies</em> или *«INSTALLDIR» (Общие7)IDE-PrivateAssemblies* с использованием файла конфигурации или разрешения сборки.

## <a name="change-reduce-registry-impact"></a>Изменение: Уменьшить влияние реестра

### <a name="global-com-registration"></a>Глобальная регистрация COM

* Ранее Visual Studio установила много ключей реестра в HKEY_CLASSES_ROOT и HKEY_LOCAL_MACHINE ульев для поддержки родной регистрации COM. Чтобы устранить это воздействие, Visual Studio теперь использует [регистрационную активацию для компонентов COM.](https://msdn.microsoft.com/library/ms973913.aspx)
* В результате, большинство файлов TLB / OLB / DLL под %ProgramFiles (x86)% -Общие файлы,Microsoft Shared-MSEnv больше не устанавливаются по умолчанию Visual Studio. Эти файлы теперь установлены в соответствии с «INSTALLDIR» с соответствующими регистрационными манифестами COM, используемыми в процессе хоста Visual Studio.
* В результате, внешний код, который опирается на глобальную регистрацию COM для интерфейсов Visual Studio COM больше не будет находить эти регистрации. Код, работающий внутри процесса Visual Studio, не видит разницы.

### <a name="visual-studio-registry"></a>Реестр визуальной студии

* Ранее Visual Studio установила много ключей реестра в **HKEY_LOCAL_MACHINE** системы и **HKEY_CURRENT_USER** ульев под visual Studio-специфический ключ:

  * **HKLM-Software-Microsoft-VisualStudio\{Version**: Ключи реестра, созданные инсталляторами MSI и расширениями для одной машины.
  * **HKCU-Software-Microsoft-VisualStudio\{Version:** Ключи реестра, созданные Visual Studio для хранения пользовательских настроек.
  * **HKCU-Software-Microsoft-VisualStudio\{Версия _Config**: Копия Visual Studio HKLM ключ выше, а также ключи реестра объединены из *файлов .pkgdef* расширений.

* Чтобы уменьшить влияние на реестр, Visual Studio теперь использует функцию [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) для хранения ключей реестра в частном двоичном файле под *«VSAPPDATA».privateregistry.bin*. В реестре системы остается лишь очень небольшое количество ключей Visual Studio.
* Существующий код, работающий внутри процесса Visual Studio, не влияет. Visual Studio перенаправит все операции реестра под ключом HKCU Visual Studio в частный реестр. Чтение и письмо в другие места регистрации будет продолжать использовать систему реестра.
* Внешний код необходимо будет загрузить и прочитать из этого файла для записей реестра Visual Studio.

### <a name="react-to-this-breaking-change"></a>Реагируйте на это нарушение изменения

* Внешний код должен быть преобразован для использования активации Без регистрации для компонентов COM.
* Внешние компоненты могут найти местоположение Visual Studio, [следуя инструкциям здесь](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Мы рекомендуем, чтобы внешние компоненты использовали [внешний менеджер настроек](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) вместо чтения/записи непосредственно в ключи реестра Visual Studio.
* Проверьте, могут ли компоненты, используемые расширением, реализовать другой метод регистрации. Например, расширения отладчика могут воспользоваться преимуществами новой [регистрации msvsmon JSON-file COM.](migrate-debugger-COM-registration.md)
