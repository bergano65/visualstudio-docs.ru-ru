---
title: Критические изменения в расширяемости Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 589f5eddb2b1e2a8fd61eea2a205f12d2d9c0742
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321360"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Изменения в расширяемости Visual Studio 2017

Visual Studio 2017 предоставляет [быстрее, облегченный установщик Visual Studio](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) , Уменьшение влияния Visual Studio на компьютерах пользователей, одновременно обеспечивая для пользователей больший выбор рабочих нагрузок и компонентов, имеющих установлен. Для поддержки этих улучшений, мы внесли изменения в модель расширяемости, включая ряд важных изменений. В этой статье описываются технические детали этих изменений и что можно сделать для их устранения.

> [!NOTE]
> Некоторые данные сведения о реализации в определенный момент времени и могут быть изменены в более поздней версии.

## <a name="changes-affecting-vsix-format-and-installation"></a>Изменения, влияющие на формат VSIX и установки

Visual Studio 2017 появилась VSIX v3 формата (версия 3) для поддержки процесса установки упрощенного.

Внесены следующие изменения в формат VSIX.

* Объявление предварительных требований для установки. Для предоставления преимуществ облегченное, Быстрая установка Visual Studio, установщик теперь предлагает больше параметров конфигурации для пользователей. Таким образом чтобы убедиться, что установлены функции и компоненты, необходимые для расширения, расширения необходимо объявить их зависимости.

  * Установщик Visual Studio 2017 автоматически предлагает получить и установить необходимые компоненты для пользователя в рамках установки расширения.
  * Пользователи также предупреждение при попытке установить расширение, которое не было создано с использованием нового формата VSIX v3, даже если они были помечены в манифесте как предназначенный для версии 15.0.

* Расширенные возможности для формата VSIX. Для доставки на [установки с минимальным влиянием на](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) Visual Studio, который также поддерживает устанавливает side-by-side, мы больше не сохраните большинство данных конфигурации в системный реестр и были перемещены в Visual Studio сборки из глобального кэша СБОРОК. Также мы увеличили возможности формата VSIX и установки модуль VSIX, что позволяет использовать его вместо MSI или EXE-файла для установки расширений для некоторых типов установки.

Новые возможности включают:

* Регистрация в указанном экземпляре Visual Studio.
* Что устанавливается за пределами [папки расширений](set-install-root.md).
* Определение архитектуры процессора.
* Зависимость от разделенных языка языковых пакетов.
* Установка с [поддержка NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Сборки расширения для Visual Studio 2017

Средства для создания нового конструктора формат манифеста VSIX v3 доступна в Visual Studio 2017. См. в соответствующем документе [как: Перенос проектов расширяемости в Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) сведения с помощью средств конструктора или внесении обновлений вручную в проект и манифест для разработки расширений VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Изменение: Путь данных пользователя Visual Studio

Ранее лишь по одному разу для каждого основного выпуска Visual Studio может существовать на каждом компьютере. Чтобы обеспечить поддержку side-by-side установленные версии Visual Studio 2017, пути к данным нескольких пользователей для Visual Studio могут существовать на компьютере пользователя.

В диспетчере параметров Visual Studio следует обновить код, выполняемый в процесс Visual Studio. Код, выполняемый вне процесса Visual Studio можно найти путь пользователя в конкретную установку Visual Studio [, следуя указаниям ниже](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Изменение: Глобальный кэш сборок (GAC)

Большинство сборок Visual Studio core больше не устанавливаются в глобальном кэше СБОРОК. Таким образом, код, выполняемый в процесс Visual Studio по-прежнему можно найти необходимые сборки во время выполнения, были внесены следующие изменения.

> [!NOTE]
> [INSTALLDIR] ниже ссылается на корневой каталог установки Visual Studio. *VSIXInstaller.exe* автоматически заполнить это, но чтобы написать пользовательский код развертывания, прочитайте [обнаружение Visual Studio](locating-visual-studio.md).

* Сборки, которые только были установлены в глобальный кэш СБОРОК:

   Теперь эти сборки устанавливаются в <em>\Common7\IDE [INSTALLDIR]\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> или *\Common7\IDE\PrivateAssemblies [INSTALLDIR]* . Эти папки являются частью пути пробы процесс Visual Studio.

* Сборки, которые были установлены в путь без проверки и в глобальный кэш СБОРОК:

   * Копия в глобальном кэше СБОРОК удалена из программы установки.
   * Объект *.pkgdef* файл был добавлен, чтобы указать запись базового кода для сборки.

      Пример:

      ```xml
      [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
      "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
      "publicKeyToken"="Public Key Token"
      "culture"="neutral"
      "version"=15.0.0.0
      ```

      Во время выполнения подсистема pkgdef Visual Studio объединяет эти записи в файл конфигурации среды выполнения в процесс Visual Studio (в разделе *[VSAPPDATA]\devenv.exe.config*) как [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) элементы. Это рекомендуемый способ позволяют найти сборку в процесс Visual Studio, так как позволяет избежать поиска с помощью проверки пути.

### <a name="reacting-to-this-breaking-change"></a>Реагирование на это критическое изменение

* Если расширение выполняется в рамках процесса Visual Studio:

   * Код будет возможность найти базовые сборки Visual Studio.
   * Рассмотрите возможность использования *.pkgdef* файл, чтобы указать путь к сборкам, при необходимости.

* Если расширение выполняется вне процесса Visual Studio:

   Попробуйте найти базовые сборки Visual Studio в разделе <em>\Common7\IDE [INSTALLDIR]\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> или *\Common7\IDE\PrivateAssemblies [INSTALLDIR]* с помощью сопоставителя файл или сборку конфигурации.

## <a name="change-reduce-registry-impact"></a>Изменение: Сокращение влияния реестра

### <a name="global-com-registration"></a>Глобальной регистрации COM

* Ранее Visual Studio устанавливается много разделов реестра в кустов HKEY_CLASSES_ROOT и HKEY_LOCAL_MACHINE, для поддержки встроенной регистрации COM. Чтобы исключить влияние этой конфигурации, Visual Studio использует [активации без регистрации для COM-компонентов](https://msdn.microsoft.com/library/ms973913.aspx).
* Как следствие, большинство TLB / OLB / DLL-файлы в % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv больше не устанавливаются по умолчанию с помощью Visual Studio. Теперь эти файлы устанавливаются в разделе [INSTALLDIR] с соответствующей манифестами Registration-Free COM, используемые в процессе размещения Visual Studio.
* В результате внешний код, который зависит от глобальной регистрации COM для интерфейсов модели COM Visual Studio больше не будет найти эти операции регистрации. Код, выполняемый в процесс Visual Studio не может заметить разницу.

### <a name="visual-studio-registry"></a>Visual Studio реестра

* Ранее установленные Visual Studio много разделов реестра в системы **HKEY_LOCAL_MACHINE** и **HKEY_CURRENT_USER** кустов в Visual Studio конкретного ключа:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}** : Разделы реестра, созданные MSI-установщики и расширений на уровне компьютера.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}** : Разделы реестра, созданные Visual Studio для хранения параметров конкретного пользователя.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Копия выше разделе Visual Studio HKLM, а также разделы реестра, перенесенных слиянием с *.pkgdef* файлы с расширениями.

* Чтобы снизить влияние на реестр, Visual Studio теперь использует [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) функции для хранения разделов реестра в закрытый двоичный файл в разделе *[VSAPPDATA]\privateregistry.bin*. Только очень небольшое количество клавиш для Visual Studio определенного остаются в системном реестре.
* Это не повлияет на существующий код, выполняемый в процесс Visual Studio. Visual Studio будет перенаправлять все операции с реестром в раздел HKCU Visual Studio конкретных частный реестр. Чтение и запись в другие места реестра будет продолжать использовать в системный реестр.
* Внешний код потребуется загрузить и прочитать из этого файла для записи реестра Visual Studio.

### <a name="react-to-this-breaking-change"></a>Реагировать на это критическое изменение

* Внешний код должен преобразовать для использования активации без регистрации для COM-компонентов также.
* Внешние компоненты можно найти в расположении Visual Studio [, следуя указаниям ниже](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Мы рекомендуем использовать внешние компоненты [внешних менеджер по параметрам](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) вместо чтения/записи, непосредственно к разделам реестра Visual Studio.
* Проверьте, может ли реализовывать другой метод для регистрации компонентов, которые использует ваше расширение. Например, можно попытаться воспользоваться преимуществами нового расширения отладчика [msvsmon регистрация JSON-файл COM](migrate-debugger-COM-registration.md).
