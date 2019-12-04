---
title: Создание приложений ClickOnce из командной строки | Документация Майкрософт
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797198"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Построение приложений ClickOnce из командной строки
В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]можно создавать проекты из командной строки, даже если они создаются в интегрированной среде разработки (IDE). На самом деле можно перестроить проект, созданный с [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], на другом компьютере, на котором установлен только .NET Framework. Это позволяет воспроизводить сборку с помощью автоматизированного процесса, например, в Центральной лаборатории построения или с помощью расширенных методик создания скриптов вне области построения самого проекта.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Воспроизведение развертываний приложений ClickOnce с помощью MSBuild
 При вызове MSBuild/target: Publish из командной строки она сообщает системе MSBuild о необходимости сборки проекта и создание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в папке Publish. Это эквивалентно выбору команды **опубликовать** в интегрированной среде разработки.

 Эта команда выполняет *файл MSBuild. exe*, который находится по пути в среде командной строки Visual Studio.

 "Целевой" — это индикатор MSBuild для обработки команды. Целевыми объектами являются целевой объект "сборка" и целевой объект "Publish". Цель сборки эквивалентна выбору команды сборки (или нажатию клавиши F5) в интегрированной среде разработки. Если требуется только построить проект, можно добиться этого, введя `msbuild`. Эта команда работает, так как целевой объект сборки является целевым объектом по умолчанию для всех проектов, создаваемых [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Это означает, что не нужно явно указывать целевой объект сборки. Таким образом, ввод `msbuild` — это та же операция, что и при вводе `msbuild /target:build`.

 Команда `/target:publish` сообщает MSBuild о необходимости вызова целевого объекта публикации. Цель публикации зависит от целевого объекта сборки. Это означает, что операция публикации является надмножеством операции сборки. Например, если вы внесли изменение в один из Visual Basic или C# исходных файлов, соответствующая сборка будет автоматически перестроена операцией публикации.

 Сведения о создании полного развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] с помощью программы командной строки Mage. exe для создания манифеста [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] см. в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Создание и построение базового приложения ClickOnce с помощью MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Создание и публикация проекта ClickOnce

1. Откройте Visual Studio и создайте новый проект.

    Выберите шаблон проекта **классическое приложение Windows** и назовите проект `CmdLineDemo`.

1. В меню **Сборка** выберите команду **опубликовать** .

    Этот шаг гарантирует правильную настройку проекта для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания приложения.

    Откроется Мастер публикации.

1. В мастере публикации нажмите кнопку **Готово**.

    Visual Studio создаст и отобразит веб-страницу по умолчанию с именем *Publish. htm*.

1. Сохраните проект и запишите расположение папки, в которой она хранится.

   Приведенные выше шаги создают проект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], который был опубликован в первый раз. Теперь можно воспроизвести сборку за пределами интегрированной среды разработки.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Воспроизведение сборки из командной строки

1. Выйдите из [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. В меню **Пуск** Windows выберите **все программы**, затем **Microsoft Visual Studio**, **инструменты Visual Studio**и **командную строку Visual Studio**. Откроется командная строка в корневой папке текущего пользователя.

3. В **командной строке Visual Studio**измените текущий каталог на расположение проекта, который вы только что создали ранее. Пример: `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Чтобы удалить существующие файлы, созданные в "Создание и публикация проекта [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]", введите `rmdir /s publish`.

    Этот шаг является необязательным, но он гарантирует, что все новые файлы были созданы сборкой из командной строки.

5. Введите `msbuild /target:publish`.

   Описанные выше действия приведут к полному развертыванию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения во вложенной папке проекта с именем **Publish**. *Кмдлинедемо. Application* — это манифест развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Папка *CmdLineDemo_1.0.0.0* содержит файлы *кмдлинедемо. exe* и *кмдлинедемо. exe. manifest*, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения. *Setup. exe* — это начальный загрузчик, который по умолчанию настроен для установки .NET Framework. Папка DotNetFX содержит распространяемые компоненты для .NET Framework. Это полный набор файлов, необходимых для развертывания приложения через Интернет или через UNC или компакт-диск или DVD-диск.
   
> [!NOTE]
> Система MSBuild использует параметр **PublishDir** для указания расположения выходных данных, например `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Параметры публикации
 При публикации приложения в описанных выше процедурах в файл проекта вставляются следующие свойства с помощью мастера публикации. Эти свойства непосредственно влияют на то, как создается [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение.

 В *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:

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

 Любое из этих свойств можно переопределить в командной строке, не изменяя сам файл проекта. Например, следующий пример приведет к построению [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания приложения без загрузчика:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Свойства публикации управляются в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] на страницах свойств **Публикация**, **Безопасность**и **подпись** **конструктора проектов**. Ниже приведено описание свойств публикации, а также сведения о том, как они заданы на различных страницах свойств конструктора приложений.

- `AssemblyOriginatorKeyFile` определяет файл ключа, используемый для подписи манифестов [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений. Этот же ключ можно также использовать для присвоения сборке строгого имени. Это свойство задается на странице **Подписывание** **конструктора проектов**.

  На странице **Безопасность** задаются следующие свойства:

- **Включить параметры безопасности ClickOnce** определяет, создаются ли [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесты. При первоначальном создании проекта [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создание манифеста отключено по умолчанию. Мастер автоматически установит этот флаг при публикации в первый раз.

- **Таржетзоне** определяет уровень доверия, который будет выдаваться в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Возможные значения: "Internet", "LocalIntranet" и "Custom". В Интернете и интрасети набор разрешений по умолчанию создается в манифесте приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Локальная интрасеть используется по умолчанию, и она по сути означает полное доверие. Custom Указывает, что только разрешения, явно указанные в файле *app. manifest* , должны быть переданы в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Файл *app. manifest* является частичным файлом манифеста, который содержит только определения сведений о доверии. Это скрытый файл, который автоматически добавляется в проект при настройке разрешений на странице **Безопасность** .

  На странице **Публикация** задаются следующие свойства:

- `PublishUrl` — это расположение, в которое приложение будет опубликовано в интегрированной среде разработки. Он вставляется в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], если не указано свойство `InstallUrl` или `UpdateUrl`.

- `ApplicationVersion` указывает версию приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Это номер версии из четырех цифр. Если последняя цифра является "*", `ApplicationRevision` заменяется на значение, вставляемое в манифест во время сборки.

- `ApplicationRevision` указывает редакцию. Это целое число, увеличивающееся каждый раз при публикации в интегрированной среде разработки. Обратите внимание, что для сборок, выполняемых в командной строке, автоматическое приращение не выполняется.

- `Install` определяет, является ли приложение установленным приложением или запущенным из веб-приложения.

- `InstallUrl` (не показано) — это расположение, откуда пользователи будут устанавливать приложение. Если это значение указано, оно будет записано в загрузчик *Setup. exe* , если свойство `IsWebBootstrapper` включено. Он также вставляется в манифест приложения, если не указано `UpdateUrl`.

- `SupportUrl` (не показано) — это расположение, связанное в диалоговом окне " **Установка и удаление программ** " для установленного приложения.

  Следующие свойства задаются в диалоговом окне **обновления приложения** , доступном на странице **Публикация** .

- `UpdateEnabled` указывает, должно ли приложение проверять наличие обновлений.

- `UpdateMode` указывает либо обновления переднего плана, либо фоновые обновления.

- `UpdateInterval` указывает, как часто приложение должно проверять наличие обновлений.

- `UpdateIntervalUnits` указывает, находится ли `UpdateInterval` значение в единицах времени, днях или неделях.

- `UpdateUrl` (не показано) — это расположение, из которого приложение будет принимать обновления. Если указано, это значение вставляется в манифест приложения.

  Следующие свойства задаются в диалоговом окне **Параметры публикации** , доступном на странице **Публикация** .

- `PublisherName` указывает имя издателя, отображаемое в строке, отображаемой при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени папки в меню " **Пуск** ".

- `ProductName` указывает имя продукта, отображаемое в строке, отображаемой при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени ярлыка в меню " **Пуск** ".

  Следующие свойства задаются в диалоговом окне **необходимые компоненты** , доступном со страницы **Публикация** .

- `BootstrapperEnabled` определяет, следует ли создавать загрузчик *Setup. exe* .

- `IsWebBootstrapper` определяет, работает ли загрузчик *Setup. exe* через Интернет или в режиме на диске.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, Публишурл и Упдатеурл
 В следующей таблице показаны четыре варианта URL-адреса для развертывания ClickOnce.

|Параметр URL-адреса|Описание|
|----------------|-----------------|
|`PublishURL`|Требуется при публикации приложения ClickOnce на веб-сайте.|
|`InstallURL`|(Необязательный аргумент) Задайте этот параметр URL-адреса, если сайт установки отличается от `PublishURL`. Например, можно задать для `PublishURL` путь FTP и задать для `InstallURL` URL-адрес.|
|`SupportURL`|(Необязательный аргумент) Задайте этот параметр URL-адреса, если сайт поддержки отличается от `PublishURL`. Например, можно установить `SupportURL` на веб-сайт поддержки клиентов вашей компании.|
|`UpdateURL`|(Необязательный аргумент) Задайте этот параметр URL-адреса, если расположение обновления отличается от `InstallURL`. Например, можно задать для `PublishURL` путь FTP и задать для `UpdateURL` URL-адрес.|

## <a name="see-also"></a>См. также:
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
