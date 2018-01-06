---
title: "Критические изменения в расширения Visual Studio 2017 г. | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 068b71a78149bb1c52e28bc47245d0dc888496bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Изменения в расширения Visual Studio 2017 г.

С помощью Visual Studio 2017 г., мы предлагаем [быстрее, облегченный возможности установки Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) определяя пользователей больше Выбор рабочих нагрузок, а также функции, которая ограничивает влияние Visual Studio на компьютерах пользователей. которые установлены. Для поддержки этих улучшений, мы внесли изменения в модель расширяемости и внесены изменения, критические расширения среды Visual Studio. В этом документе описываются технические детали этих изменений, и что можно сделать, чтобы их устранения. Обратите внимание, что некоторые данные в момент реализации и может быть изменен.

## <a name="changes-affecting-vsix-format-and-installation"></a>Изменения, влияющие на формат VSIX и установки

Мы рассматриваем VSIX v3 формате (версия 3) для поддержки взаимодействия установки недоступно.

Имеются следующие изменения в формате VSIX.

* Описание необходимых компонентов установки. Для доставки на объект promise компактное fast установка Visual Studio, установщик теперь поддерживает дополнительные параметры конфигурации для пользователей. В результате Чтобы установить компоненты, необходимые для расширения, расширения потребуется объявлять их зависимости.
  * Установщик Visual Studio 2017 г. будет автоматически предлагать получить и установить необходимые компоненты для пользователя в рамках установки расширения.
  * При попытке установить расширение, не был построен с использованием нового формата VSIX v3, даже если они были помечены в манифестах как назначение целевой версии 15.0 пользователей также предупреждение.
* Улучшенные возможности для формата VSIX. Для доставки на [и щадящих установки](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) Visual Studio, который также поддерживает устанавливает side-by-side, мы больше не сохраните большую часть данных конфигурации в системный реестр и были перемещены в Visual Studio сборки из глобального кэша СБОРОК. Мы также увеличивается возможности формата VSIX и программы установки VSIX, что позволяет использовать его вместо MSI-файла или exe-ФАЙЛ для установки расширений для некоторых типов установки.

  Новые возможности включают:

  * Регистрация в указанном экземпляре Visual Studio.
  * Установки вне [папку extensions](set-install-root.md).
  * Определение архитектуры процессора.
  * Зависимость от запятыми языка языковых пакетов.
  * Установка с [поддержка NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Создание расширения для Visual Studio 2017 г.

Средства для создания нового конструктора формат манифеста VSIX v3 теперь доступна в Visual Studio 2017 г. См. в соответствующем документе [как: перенос проектов расширяемости для Visual Studio 2017 г](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) Подробнее об использовании средства конструктора или внесении обновлений вручную в проект и манифест для разработки расширений VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Изменения: Путь к данным пользователя Visual Studio

Ранее только одна копия каждой основной версии Visual Studio может присутствовать на каждом компьютере. Для поддержки side-by-side установки Visual Studio 2017 г., пути к данным нескольких пользователей для Visual Studio могут существовать на компьютере пользователя.

Чтобы использовать диспетчер параметров Visual Studio должен быть обновлен кодом, выполняемым внутри процесса Visual Studio. Код, выполняющийся вне процесса Visual Studio можно найти путь пользователя конкретного экземпляра Visual Studio [, следуя инструкциям ниже](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Изменение: Глобальный кэш сборок (GAC)

Большинство основных сборок Visual Studio больше не устанавливаются в глобальном кэше СБОРОК. Таким образом, код, выполняемый процесс Visual Studio по-прежнему можно найти необходимые сборки во время выполнения, были внесены следующие изменения.

> [!NOTE]
> [INSTALLDIR] ниже ссылается на корневой каталог установки Visual Studio. VSIXInstaller.exe автоматически будет заполнять это, но также для создания кода пользовательское развертывание, прочитайте [обнаружение Visual Studio](locating-visual-studio.md).

* Сборки, которые только были установлены в глобальный кэш СБОРОК:
  * Теперь эти сборки устанавливаются в \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies или \Common7\IDE\PrivateAssemblies [INSTALLDIR]. Эти папки являются частью пути поиска сборок процесс Visual Studio.
* Сборки, которые были установлены в путь без проверки и в глобальный кэш СБОРОК:
  * Копировать в глобальном кэше СБОРОК был удален из программы установки.
  * Pkgdef-файл был добавлен для указания записи базы кода для сборки.

    Пример:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Во время выполнения подсистема pkgdef Visual Studio объединит эти записи в файл конфигурации среды выполнения процесса Visual Studio (в разделе [VSAPPDATA]\devenv.exe.config) как [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) элементов. Это рекомендуемый способ разрешить процесс Visual Studio найти сборку, так как позволяет избежать проверки пути поиска.

### <a name="reacting-to-this-breaking-change"></a>Отклик на это критическое изменение

* Если расширение выполняется в рамках процесса Visual Studio:
  * Код смогут найти основных сборок Visual Studio.
  * Рассмотрите возможность использования pkgdef-файл для указания пути к сборкам, при необходимости.
* Если расширение выполняется вне процесса Visual Studio:
  * Попробуйте найти основных сборок Visual Studio в разделе [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies или \Common7\IDE\PrivateAssemblies [INSTALLDIR] с помощью сопоставителя конфигурации файла или сборки.

## <a name="change-reduce-registry-impact"></a>Изменение: Снизить влияние конфигурации реестра

### <a name="global-com-registration"></a>Глобальные регистрации COM

* Ранее Visual Studio установлен много разделов реестра в кустов HKEY_CLASSES_ROOT и HKEY_LOCAL_MACHINE, для поддержки собственного регистрации COM. Чтобы снизить влияние этой конфигурации, Visual Studio использует [активации без регистрации для COM-компонентов](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Таким образом, большинство TLB / OLB / DLL-файлы в % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv больше не устанавливаются по умолчанию в Visual Studio. Теперь эти файлы устанавливаются в разделе [INSTALLDIR] с соответствующей COM без регистрации манифестов, используемых в процессе размещения Visual Studio.
* В результате внешний код, который зависит от глобальной регистрации COM для Visual Studio COM-интерфейсов, больше не найдет регистрацию. Кодом, выполняемым внутри процесса Visual Studio не может заметить разницу.

### <a name="visual-studio-registry"></a>Visual Studio реестра

* Ранее Visual Studio установлены много разделов реестра в системе HKEY_LOCAL_MACHINE и HKEY_CURRENT_USER кустов внутри Visual Studio определенного раздела:
  * HKLM\Software\Microsoft\VisualStudio\\**версии**: разделы реестра, созданные установщик MSI и расширения на уровне компьютера.
  * HKCU\Software\Microsoft\VisualStudio\\**версии**: разделы реестра, созданные с помощью Visual Studio для хранения параметров конкретного пользователя.
  * HKCU\Software\Microsoft\VisualStudio\\**версии**_Config: объединить копии выше разделе Visual Studio HKLM, а также разделы реестра из файлов .pkgdef путем расширения.
* Чтобы снизить влияние на реестр, Visual Studio использует [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) функции для хранения разделов реестра в частной двоичного файла в разделе [VSAPPDATA]\privateregistry.bin. Только очень небольшое количество клавиш для Visual Studio определенного остаются в системном реестре.
* Это не повлияет на существующие кодом, выполняемым внутри процесса Visual Studio. Visual Studio выполнит перенаправление все операции реестра в разделе HKCU Visual Studio конкретного частного реестра. Чтение и запись в других расположениях в реестре будет продолжать использовать системный реестр.
* Внешний код будет необходимо загрузить и считываются из этого файла для записи реестра Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Отклик на это критическое изменение

* Для активации без регистрации для COM-компонентов также следует преобразовать внешний код.
* Внешние компоненты можно найти расположение Visual Studio [, следуя инструкциям ниже](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Мы рекомендуем использовать внешние компоненты [внешних менеджер по параметрам](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) вместо чтения/записи, непосредственно к разделам реестра Visual Studio.
* Проверьте, может ли реализовывать другим способом регистрации компонентов, которые использует расширение. Например, расширения отладчика можно воспользоваться преимуществами нового [msvsmon регистрации COM JSON-файл](migrate-debugger-COM-registration.md).
