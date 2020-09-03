---
title: Создание приложений ClickOnce из командной строки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2625a8d4caa7dd53e9ce86395a98622f91d686b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155715"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Построение ClickOnce-приложений из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] можно создавать проекты из командной строки, даже если они создаются в интегрированной среде разработки (IDE). На самом деле можно перестроить проект, созданный с помощью, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] на другом компьютере, на котором [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] установлена только установка. Это позволяет воспроизводить сборку с помощью автоматизированного процесса, например, в Центральной лаборатории построения или с помощью расширенных методик создания скриптов вне области построения самого проекта.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Использование MSBuild для воспроизведения развертываний приложений ClickOnce  
 При вызове MSBuild/target: Publish из командной строки она сообщает системе MSBuild о необходимости построить проект и создать [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение в папке Publish. Это эквивалентно выбору команды **опубликовать** в интегрированной среде разработки.  
  
 Эта команда выполняет msbuild.exe, которая находится по пути в среде командной строки Visual Studio.  
  
 "Целевой" — это индикатор MSBuild для обработки команды. Целевыми объектами являются целевой объект "сборка" и целевой объект "Publish". Цель сборки эквивалентна выбору команды сборки (или нажатию клавиши F5) в интегрированной среде разработки. Если требуется только построить проект, можно добиться этого, введя `msbuild` . Эта команда работает, так как целевой объект сборки является целевым объектом по умолчанию для всех проектов, создаваемых [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Это означает, что не нужно явно указывать целевой объект сборки. Таким образом, ввод `msbuild` — это та же операция, что и при вводе `msbuild /target:build` .  
  
 `/target:publish`Команда сообщает MSBuild о необходимости вызова целевого объекта публикации. Цель публикации зависит от целевого объекта сборки. Это означает, что операция публикации является надмножеством операции сборки. Например, если вы внесли изменения в один из исходных файлов Visual Basic или C#, соответствующая сборка будет автоматически перестроена операцией публикации.  
  
 Сведения о создании полного [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания с помощью программы командной строки Mage.exe для создания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифеста см. в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Создание и сборка базового приложения ClickOnce с помощью MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Создание и публикация проекта ClickOnce  
  
1. В меню **файл** выберите пункт **создать проект** . Откроется диалоговое окно **Новый проект** .  
  
2. Выберите **приложение Windows** и назовите его `CmdLineDemo` .  
  
3. В меню **Сборка** выберите команду **опубликовать** .  
  
    Этот шаг обеспечивает правильную настройку проекта для создания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания приложения.  
  
    Откроется Мастер публикации.  
  
4. В мастере публикации нажмите кнопку **Готово**.  
  
    Visual Studio создаст и отобразит веб-страницу по умолчанию с именем Publish.htm.  
  
5. Сохраните проект и запишите расположение папки, в которой она хранится.  
  
   Приведенные выше шаги создают [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] проект, который был опубликован в первый раз. Теперь можно воспроизвести сборку за пределами интегрированной среды разработки.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Воспроизведение сборки из командной строки  
  
1. Выйдите из [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. В меню **Пуск** Windows выберите **все программы**, затем **Microsoft Visual Studio**, **инструменты Visual Studio**и **командную строку Visual Studio**. Откроется командная строка в корневой папке текущего пользователя.  
  
3. В **командной строке Visual Studio**измените текущий каталог на расположение проекта, который вы только что создали ранее. Например, введите `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Чтобы удалить существующие файлы, созданные в "Создание и публикация проекта" [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , введите `rmdir /s publish` .  
  
    Этот шаг является необязательным, но он гарантирует, что все новые файлы были созданы сборкой из командной строки.  
  
5. Введите `msbuild /target:publish`.  
  
   Описанные выше действия приведут к полному [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертыванию приложения во вложенной папке проекта с именем **Publish**. Кмдлинедемо. Application — это [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест развертывания. Папка CmdLineDemo_1.0.0.0 содержит файлы CmdLineDemo.exe и файл CmdLineDemo.exe. manifest, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Setup.exe является загрузчиком, который по умолчанию настроен для установки [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Папка DotNetFX содержит распространяемые компоненты для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Это полный набор файлов, необходимых для развертывания приложения через Интернет или через UNC или компакт-диск или DVD-диск.  
  
## <a name="publishing-properties"></a>Свойства публикации  
 При публикации приложения в описанных выше процедурах в файл проекта вставляются следующие свойства с помощью мастера публикации. Эти свойства непосредственно влияют на то, как создается [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение.  
  
 В Кмдлинедемо. vbproj/Кмдлинедемо. csproj:  
  
```  
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
  
 Любое из этих свойств можно переопределить в командной строке, не изменяя сам файл проекта. Например, ниже будет построено [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывание приложения без загрузчика:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Управление свойствами публикации осуществляется на [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] страницах свойств **Публикация**, **Безопасность**и **подпись** **конструктора проектов**. Ниже приведено описание свойств публикации, а также сведения о том, как они заданы на различных страницах свойств конструктора приложений.  
  
- `AssemblyOriginatorKeyFile` Определяет файл ключа, используемый для подписи [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифестов приложения. Этот же ключ можно также использовать для присвоения сборке строгого имени. Это свойство задается на странице **Подписывание** **конструктора проектов**.  
  
  На странице **Безопасность** задаются следующие свойства:  
  
- **Включить параметры безопасности ClickOnce** определяет [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , создаются ли манифесты. При первоначальном создании проекта [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Создание манифеста по умолчанию отключено. Мастер автоматически установит этот флаг при публикации в первый раз.  
  
- **Таржетзоне** определяет уровень доверия, который будет выдаваться в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Возможные значения: "Internet", "LocalIntranet" и "Custom". В Интернете и интрасети набор разрешений по умолчанию создается в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте приложения. Локальная интрасеть используется по умолчанию, и она по сути означает полное доверие. Custom Указывает, что только разрешения, явно указанные в файле App. manifest, должны быть переданы в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Файл App. manifest является частичным файлом манифеста, который содержит только определения сведений о доверии. Это скрытый файл, который автоматически добавляется в проект при настройке разрешений на странице **Безопасность** .  
  
  На странице **Публикация** задаются следующие свойства:  
  
- `PublishUrl` — Это расположение, в котором приложение будет опубликовано в интегрированной среде разработки. Он вставляется в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения, если `InstallUrl` `UpdateUrl` не указано ни свойство, ни.  
  
- `ApplicationVersion` Указывает версию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Это номер версии из четырех цифр. Если последняя цифра является "*", то `ApplicationRevision` вместо значения, вставляемого в манифест, во время сборки заменяется.  
  
- `ApplicationRevision` указывает редакцию. Это целое число, увеличивающееся каждый раз при публикации в интегрированной среде разработки. Обратите внимание, что для сборок, выполняемых в командной строке, автоматическое приращение не выполняется.  
  
- `Install` Определяет, является ли приложение установленным приложением или запущенным из веб-приложения.  
  
- `InstallUrl` (не показано) — это расположение, откуда пользователи будут устанавливать приложение. Если это значение указано, оно записывается в начальный загрузчик setup.exe, если `IsWebBootstrapper` свойство включено. Он также вставляется в манифест приложения, если параметр `UpdateUrl` не указан.  
  
- `SupportUrl` (не показано) — это расположение, связанное в диалоговом окне " **Установка и удаление программ** " для установленного приложения.  
  
  Следующие свойства задаются в диалоговом окне **обновления приложения** , доступном на странице **Публикация** .  
  
- `UpdateEnabled` Указывает, должно ли приложение проверять наличие обновлений.  
  
- `UpdateMode` Задает обновления переднего плана или фоновые обновления.  
  
- `UpdateInterval` Указывает, как часто приложение должно проверять наличие обновлений.  
  
- `UpdateIntervalUnits` Указывает, `UpdateInterval` находится ли значение в единицах времени, днях или неделях.  
  
- `UpdateUrl` (не показано) — это расположение, из которого приложение будет принимать обновления. Если указано, это значение вставляется в манифест приложения.  
  
- Следующие свойства задаются в диалоговом окне **Параметры публикации** , доступном на странице **Публикация** .  
  
- `PublisherName` Указывает имя издателя, отображаемое в приглашении, которое отображается при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени папки в меню " **Пуск** ".  
  
- `ProductName` Указывает имя продукта, отображаемое в приглашении, которое отображается при установке или запуске приложения. В случае установленного приложения оно также используется для указания имени ярлыка в меню " **Пуск** ".  
  
- Следующие свойства задаются в диалоговом окне **необходимые компоненты** , доступном со страницы **Публикация** .  
  
- `BootstrapperEnabled` Определяет, следует ли создавать начальный загрузчик setup.exe.  
  
- `IsWebBootstrapper` Определяет, работает ли загрузчик setup.exe в Интернете или в режиме на диске.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, Публишурл и Упдатеурл  
 В следующей таблице показаны четыре варианта URL-адреса для развертывания ClickOnce.  
  
|Параметр URL-адреса|Описание|  
|----------------|-----------------|  
|`PublishURL`|Требуется при публикации приложения ClickOnce на веб-сайте.|  
|`InstallURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если сайт установки отличается от `PublishURL` . Например, можно присвоить параметру `PublishURL` путь FTP и задать для него `InstallURL` URL-адрес.|  
|`SupportURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если сайт поддержки отличается от `PublishURL` . Например, можно установить на `SupportURL` веб-сайт поддержки клиентов вашей компании.|  
|`UpdateURL`|Необязательный элемент. Задайте этот параметр URL-адреса, если расположение обновления отличается от `InstallURL` . Например, можно присвоить параметру `PublishURL` путь FTP и задать для него `UpdateURL` URL-адрес.|  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Безопасность и развертывание ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
