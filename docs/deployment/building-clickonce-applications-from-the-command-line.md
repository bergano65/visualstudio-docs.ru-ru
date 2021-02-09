---
title: Создание приложений ClickOnce из командной строки | Документация Майкрософт
description: Узнайте, как создавать проекты Visual Studio из командной строки, что позволяет воспроизвести сборку с помощью автоматизированного процесса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 13b057f0a688c3a1ae855215ac226a4d31993ea1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895158"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Построение приложений ClickOnce из командной строки

В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] можно создавать проекты из командной строки, даже если они создаются в интегрированной среде разработки (IDE). На самом деле можно перестроить проект, созданный с помощью, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] на другом компьютере, на котором установлен только платформа .NET Framework. Это позволяет воспроизводить сборку с помощью автоматизированного процесса, например, в Центральной лаборатории построения или с помощью расширенных методик создания скриптов вне области построения самого проекта.

## <a name="use-msbuild-to-reproduce-net-framework-clickonce-application-deployments"></a>Воспроизведение платформа .NET Framework развертываний приложений ClickOnce с помощью MSBuild

 При вызове MSBuild/target: Publish из командной строки она сообщает системе MSBuild о необходимости построить проект и создать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение в папке Publish. Это эквивалентно выбору команды **опубликовать** в интегрированной среде разработки.

 Эта команда выполняет *msbuild.exe*, которая находится по пути в среде командной строки Visual Studio.

 "Целевой" — это индикатор MSBuild для обработки команды. Целевыми объектами являются целевой объект "сборка" и целевой объект "Publish". Цель сборки эквивалентна выбору команды сборки (или нажатию клавиши F5) в интегрированной среде разработки. Если требуется только построить проект, можно добиться этого, введя `msbuild` . Эта команда работает, так как целевой объект сборки является целевым объектом по умолчанию для всех проектов, создаваемых [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . Это означает, что не нужно явно указывать целевой объект сборки. Таким образом, ввод `msbuild` — это та же операция, что и при вводе `msbuild /target:build` .

 `/target:publish`Команда сообщает MSBuild о необходимости вызова целевого объекта публикации. Цель публикации зависит от целевого объекта сборки. Это означает, что операция публикации является надмножеством операции сборки. Например, если вы внесли изменения в один из исходных файлов Visual Basic или C#, соответствующая сборка будет автоматически перестроена операцией публикации.

 Сведения о создании полного [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания с помощью программы командной строки Mage.exe для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифеста см. в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Создание и построение базового приложения ClickOnce с помощью MSBuild

### <a name="to-create-and-publish-a-clickonce-project"></a>Создание и публикация проекта ClickOnce

1. Откройте Visual Studio и создайте новый проект.

    Выберите шаблон проекта **классическое приложение Windows** и укажите имя проекта `CmdLineDemo` .

1. В меню **Сборка** выберите команду **опубликовать** .

    Этот шаг обеспечивает правильную настройку проекта для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания приложения.

    Откроется Мастер публикации.

1. В мастере публикации нажмите кнопку **Готово**.

    Visual Studio создаст и отобразит веб-страницу по умолчанию с именем *Publish.htm*.

1. Сохраните проект и запишите расположение папки, в которой она хранится.

   Приведенные выше шаги создают [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] проект, который был опубликован в первый раз. Теперь можно воспроизвести сборку за пределами интегрированной среды разработки.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Воспроизведение сборки из командной строки

1. Выйдите из [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. В меню **Пуск** Windows выберите **все программы**, затем **Microsoft Visual Studio**, **инструменты Visual Studio** и **командную строку Visual Studio**. Откроется командная строка в корневой папке текущего пользователя.

3. В **командной строке Visual Studio** измените текущий каталог на расположение проекта, который вы только что создали ранее. Например, введите `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Чтобы удалить существующие файлы, созданные в "Создание и публикация проекта" [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , введите `rmdir /s publish` .

    Этот шаг является необязательным, но он гарантирует, что все новые файлы были созданы сборкой из командной строки.

5. Введите `msbuild /target:publish`.

   Описанные выше действия приведут к полному [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертыванию приложения во вложенной папке проекта с именем **Publish**. *Кмдлинедемо. Application* — это [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Папка *CmdLineDemo_1.0.0.0* содержит файлы *CmdLineDemo.exe* и файл *CmdLineDemo.exe. manifest*, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения. *Setup.exe* является загрузчиком, который по умолчанию настроен для установки платформа .NET Framework. Папка DotNetFX содержит распространяемые компоненты для платформа .NET Framework. Это полный набор файлов, необходимых для развертывания приложения через Интернет или через UNC или компакт-диск или DVD-диск.

> [!NOTE]
> Система MSBuild использует параметр **PublishDir** для указания расположения выходных данных, например `msbuild /t:publish /p:PublishDir="<specific location>"` .

::: moniker range=">=vs-2019"

## <a name="build-net-clickonce-applications-from-the-command-line"></a>Создание приложений .NET ClickOnce из командной строки

Создание приложений .NET ClickOnce из командной строки аналогично тому, за исключением того, что необходимо предоставить дополнительное свойство для профиля публикации в командной строке MSBuild. Самый простой способ создать профиль публикации — использовать Visual Studio.  Дополнительные сведения см. [в статье Развертывание приложения Windows на платформе .NET с помощью ClickOnce](quickstart-deploy-using-clickonce-folder.md) .

После создания профиля публикации можно предоставить файл pubxml как свойство в командной строке MSBuild. Пример:

```cmd
    msbuild /t:publish /p:PublishProfile=<pubxml file> /p:PublishDir="<specific location>"
```
::: moniker-end

## <a name="publish-properties"></a>Параметры публикации

 При публикации приложения в описанных выше процедурах в файл проекта вставляются следующие свойства: Мастер публикации или файл профиля публикации для проектов .NET Core 3,1 или более поздней версии. Эти свойства непосредственно влияют на то, как создается [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение.

 В *кмдлинедемо. vbproj*  /  *кмдлинедемо. csproj*:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Для проектов платформа .NET Framework можно переопределить любое из этих свойств в командной строке, не изменяя сам файл проекта. Например, ниже будет построено [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывание приложения без загрузчика:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
 ```

::: moniker range=">=vs-2019"
Для .NET Core 3,1 или более поздних версий эти параметры предоставляются в файле pubxml.

 Управление свойствами публикации осуществляется на [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] страницах свойств **Публикация**, **Безопасность** и **подпись** **конструктора проектов**. Ниже приведено описание свойств публикации, а также сведения о том, как они заданы на различных страницах свойств конструктора приложений.

> [!NOTE]
> Для проектов Windows для настольных компьютеров эти параметры теперь находятся в мастере публикации.
::: moniker-end

- `AssemblyOriginatorKeyFile` Определяет файл ключа, используемый для подписи [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифестов приложения. Этот же ключ можно также использовать для присвоения сборке строгого имени. Это свойство задается на странице **Подписывание** **конструктора проектов**.
::: moniker range=">=vs-2019"
Для приложений Windows .NET этот параметр остается в файле проекта
::: moniker-end

  На странице **Безопасность** задаются следующие свойства:

- **Включить параметры безопасности ClickOnce** определяет [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , создаются ли манифесты. При первоначальном создании проекта [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Создание манифеста по умолчанию отключено. Мастер автоматически установит этот флаг при публикации в первый раз.

- **Таржетзоне** определяет уровень доверия, который будет выдаваться в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения. Возможные значения: "Internet", "LocalIntranet" и "Custom". В Интернете и интрасети набор разрешений по умолчанию создается в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте приложения. Локальная интрасеть используется по умолчанию, и она по сути означает полное доверие. Custom Указывает, что только разрешения, явно указанные в файле *app. manifest* , должны быть переданы в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения. Файл *app. manifest* является частичным файлом манифеста, который содержит только определения сведений о доверии. Это скрытый файл, который автоматически добавляется в проект при настройке разрешений на странице **Безопасность** .
-
::: moniker range=">=vs-2019"
> [!NOTE]
> Для .NET Core 3,1 или более поздних версий проекты Windows для настольных компьютеров эти параметры безопасности не поддерживаются.
::: moniker-end

  На странице **Публикация** задаются следующие свойства:

- `PublishUrl` — Это расположение, в котором приложение будет опубликовано в интегрированной среде разработки. Он вставляется в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения, если `InstallUrl` `UpdateUrl` не указано ни свойство, ни.

- `ApplicationVersion` Указывает версию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Это номер версии из четырех цифр. Если последняя цифра является "*", то `ApplicationRevision` вместо значения, вставляемого в манифест, во время сборки заменяется.

- `ApplicationRevision` указывает редакцию. Это целое число, увеличивающееся каждый раз при публикации в интегрированной среде разработки. Обратите внимание, что для сборок, выполняемых в командной строке, автоматическое приращение не выполняется.

- `Install` Определяет, является ли приложение установленным приложением или запущенным из веб-приложения.

- `InstallUrl` (не показано) — это расположение, откуда пользователи будут устанавливать приложение. Если это значение указано, оно записывается в начальный загрузчик *setup.exe* , если `IsWebBootstrapper` свойство включено. Он также вставляется в манифест приложения, если параметр `UpdateUrl` не указан.

- `SupportUrl` (не показано) — это расположение, связанное в диалоговом окне " **Установка и удаление программ** " для установленного приложения.

  Следующие свойства задаются в диалоговом окне **обновления приложения** , доступном на странице **Публикация** .

- `UpdateEnabled` Указывает, должно ли приложение проверять наличие обновлений.

- `UpdateMode` Задает обновления переднего плана или фоновые обновления.
::: moniker range=">=vs-2019"
   Для .NET Core 3,1 или более поздних версий проекты, фон не поддерживается.  
::: moniker-end
- `UpdateInterval` Указывает, как часто приложение должно проверять наличие обновлений.
::: moniker range=">=vs-2019"
   Для .NET Core 3,1 или более поздней версии этот параметр не поддерживается.
::: moniker-end

- `UpdateIntervalUnits` Указывает, `UpdateInterval` находится ли значение в единицах времени, днях или неделях.
::: moniker range=">=vs-2019"
   Для .NET Core 3,1 или более поздней версии этот параметр не поддерживается.
::: moniker-end

- `UpdateUrl` (не показано) — это расположение, из которого приложение будет принимать обновления. Если указано, это значение вставляется в манифест приложения.

  Следующие свойства задаются в диалоговом окне **Параметры публикации** , доступном на странице **Публикация** .

- `PublisherName` Указывает имя издателя, отображаемое в приглашении, которое отображается при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени папки в меню " **Пуск** ".

- `ProductName` Указывает имя продукта, отображаемое в приглашении, которое отображается при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени ярлыка в меню " **Пуск** ".

  Следующие свойства задаются в диалоговом окне **необходимые компоненты** , доступном со страницы **Публикация** .

- `BootstrapperEnabled` Определяет, следует ли создавать начальный загрузчик *setup.exe* .

- `IsWebBootstrapper` Определяет, работает ли загрузчик *setup.exe* в Интернете или в режиме на диске.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, Публишурл и Упдатеурл

 В следующей таблице показаны четыре варианта URL-адреса для развертывания ClickOnce.

|Параметр URL-адреса|Описание|
|----------------|-----------------|
|`PublishURL`|Требуется при публикации приложения ClickOnce на веб-сайте.|
|`InstallURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если сайт установки отличается от `PublishURL` . Например, можно присвоить параметру `PublishURL` путь FTP и задать для него `InstallURL` URL-адрес.|
|`SupportURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если сайт поддержки отличается от `PublishURL` . Например, можно установить на `SupportURL` веб-сайт поддержки клиентов вашей компании.|
|`UpdateURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если расположение обновления отличается от `InstallURL` . Например, можно присвоить параметру `PublishURL` путь FTP и задать для него `UpdateURL` URL-адрес.|

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
