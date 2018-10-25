---
title: Построение ClickOnce-приложений из командной строки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: dac26a7846f4a6b611c53e9cd537d112a8205d2f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836792"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Построение ClickOnce-приложений из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], можно построить проекты из командной строки, даже если они созданы в интегрированной среде разработки (IDE). На самом деле, можно перестроить проект, созданный с помощью [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] на другом компьютере, имеющем только [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] установлен. Благодаря этому можно воспроизвести с помощью автоматизированного процесса сборки, например, при построении центра лабораторий или с помощью расширенные методы написания сценариев вне области построения самого проекта.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Использование MSBuild для воспроизведения развертывания приложений ClickOnce  
 При вызове msbuild/target: Publish, в командной строке, он сообщает системе MSBuild для сборки проекта и создания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения в папке публикации. Это эквивалентно выбору **публикации** в интегрированной среде разработки.  
  
 Эта команда выполняет msbuild.exe, которая находится на пути в среде командной строки Visual Studio.  
  
 «target» является показателем в MSBuild о том, как обработать команду. Основные цели будут целевой объект «сборка» и «опубликовать» целевой объект. Целевой объект построения является эквивалентом выбору построения команды (или нажав клавишу F5), в интегрированной среде разработки. Если требуется выполнить сборку проекта, этого можно, введя `msbuild`. Эта команда работает, поскольку целевой объект построения является целевым объектом по умолчанию для всех проектов, созданных [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Это означает, что не нужно явно указать целевой объект построения. Таким образом, введя `msbuild` выполняется та же операция, как ввести `msbuild /target:build`.  
  
 `/target:publish` Команда сообщает MSBuild о необходимости вызова место назначения публикации. Целевой объект публикации зависит от целевой сборки. Это означает, что операция публикации является надмножеством операции построения. Например если вы внесли изменения в один из исходных файлов Visual Basic или C#, соответствующей сборке будет автоматически перестроить с операции публикации.  
  
 Сведения о создании полной [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания, используя средство командной строки Mage.exe для создания вашего [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест, см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Создание и построение основные ClickOnce-приложения с помощью MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Чтобы создать и опубликовать проект ClickOnce  
  
1. Нажмите кнопку **новый проект** из **файл** меню. Откроется диалоговое окно **Новый проект** .  
  
2. Выберите **приложения Windows** и назовите его `CmdLineDemo`.  
  
3. Из **построения** меню, щелкните **публикации** команды.  
  
    Этот шаг гарантирует, что проект правильно настроен для составления [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания приложения.  
  
    Откроется Мастер публикации.  
  
4. В мастере публикации, нажмите кнопку **Готово**.  
  
    Visual Studio создает и отображает веб-страницы по умолчанию, именем Publish.htm.  
  
5. Сохраните проект и запишите расположение папки, в которой будет храниться.  
  
   Выше описаны действия по созданию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] проекта, опубликованный в первый раз. Теперь можно воспроизвести построение вне интегрированной среды разработки.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Воспроизведение построения из командной строки  
  
1. Выйдите из [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. Из Windows **запустить** меню, нажмите кнопку **все программы**, затем **Microsoft Visual Studio**, затем **средств Visual Studio**, а затем **Командная строка visual Studio**. Это следует открыть командную строку в корневой папке текущего пользователя.  
  
3. В **Командная строка Visual Studio**, перейдите в расположение проекта, вы только что выполнили выше текущий каталог. Например, введите `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Чтобы удалить существующие файлы, созданные в «для создания и публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] проекта,» тип `rmdir /s publish`.  
  
    Этот шаг необязателен, но это гарантирует, что новые файлы были все созданные сборкой командной строки.  
  
5. Введите `msbuild /target:publish`.  
  
   Описанные выше действия создадут полное [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания приложения во вложенной папке проекта с именем P**бликация**. — CmdLineDemo.application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест развертывания. Папка CmdLineDemo_1.0.0.0 содержит файлы CmdLineDemo.exe и CmdLineDemo.exe.manifest, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Setup.exe является загрузчиком, который по умолчанию настроен на установку [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Папка DotNetFX содержит распространяемые компоненты для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Это весь набор файлов, необходимых для развертывания приложения через Интернет или с помощью UNC-путь или CD/DVD.  
  
## <a name="publishing-properties"></a>Свойства публикации  
 При публикации приложения в приведенных выше процедурах, следующие свойства будут вставлены в файле проекта с помощью мастера публикации. Эти свойства непосредственно влияют на способ [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] создается приложение.  
  
 В CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
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
  
 Вы можете переопределить любое из этих свойств в командной строке не изменяя сам файл проекта. Например, следующая команда выполняет построение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания приложения без загрузчика:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Свойства публикации контролируются в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] из **публикации**, **безопасности**, и **подписывание** страниц свойств **конструктора проектов** . Ниже приводится описание свойств публикации, а также Индикация того, как каждый задается на различных страницах свойств конструктора приложений.  
  
- `AssemblyOriginatorKeyFile` Определяет файл ключа, используемого для подписания вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесты приложения. Этот же ключ также может использоваться для назначения строгого имени сборки. Это свойство задается на **подписывание** странице **конструктор проектов**.  
  
  Следующие свойства задаются на **безопасности** страницы:  
  
- **Включить параметры безопасности ClickOnce-приложений** определяет ли [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифестов. При создании проекта, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] создания манифеста по умолчанию отключены. Мастер автоматически устанавливает этот флаг при публикации в первый раз.  
  
- **TargetZone** определяет уровень доверия, передаваемый в вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Возможные значения: «Интернет», «Локальная интрасеть» и «Custom». Интернет и интрасеть вызовет набор разрешений по умолчанию передаются в вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. По умолчанию — LocalIntranet и по сути означает полное доверие. Настройка указывает, что только разрешения, явно указанного в файле app.manifest должны предоставляться в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Файл app.manifest является частичного файл манифеста, который содержит только определения сведений о доверии. Он является скрытым, автоматически добавляется в проект при настройке разрешений на **безопасности** страницы.  
  
  Следующие свойства задаются на **публикации** страницы:  
  
- `PublishUrl` — Это расположение, где приложение будет публиковаться в интегрированной среде разработки. Он будет вставлен в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения, если ни один из `InstallUrl` или `UpdateUrl` указано свойство.  
  
- `ApplicationVersion` Указывает версию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Это номер версии из четырех цифр. Если последний знак «*», а затем `ApplicationRevision` заменяется значением, вставленным в манифест во время сборки.  
  
- `ApplicationRevision` Указывает редакцию. Это должно быть целым числом, который увеличивается каждый раз при публикации в интегрированной среде разработки. Обратите внимание на то, что оно не увеличивается автоматически для сборок, выполняемые в командной строке.  
  
- `Install` Определяет, является ли приложение установленным или выполнения из веб-приложения.  
  
- `InstallUrl` (не показано) — расположение, где пользователи будут устанавливать приложение из. Если указано, это значение оно записывается в файл-загрузчик setup.exe, если `IsWebBootstrapper` включено свойство. Он также вставляется в манифест приложения, если `UpdateUrl` не указан.  
  
- `SupportUrl` (не показано) расположение связанного в **Add/Remove Programs** диалоговое окно для установленного приложения.  
  
  Следующие свойства задаются в **обновления приложения** диалоговое окно, открывается из **публикации** страницы.  
  
- `UpdateEnabled` Указывает, должно ли приложение проверять наличие обновлений.  
  
- `UpdateMode` Указывает, выполняются обновления или обновления в фоновом режиме.  
  
- `UpdateInterval` Указывает, как часто приложение должно проверять наличие обновлений.  
  
- `UpdateIntervalUnits` Указывает, является ли `UpdateInterval` значение измеряется в часах, днях или неделях.  
  
- `UpdateUrl` (не показано) — расположение, из которой приложение будет получать обновления. Если указано, оно вставляется в манифест приложения.  
  
- Следующие свойства задаются в **параметры публикации** диалоговое окно, открывается из **публикации** страницы.  
  
- `PublisherName` Задает имя издателя, отображаемое в командной строке при установке или запуске приложения. В случае установленного приложения также используется для указания имени папки на **запустить** меню.  
  
- `ProductName` Задает имя продукта, отображаемое в командной строке при установке или запуске приложения. В случае установленного приложения также используется для указания имени ярлыка на **запустить** меню.  
  
- Следующие свойства задаются в **предварительные требования** диалоговое окно, открывается из **публикации** страницы.  
  
- `BootstrapperEnabled` Определяет, следует ли создавать файл-загрузчик setup.exe.  
  
- `IsWebBootstrapper` Определяет, работает ли загрузчик setup.exe в Интернете или в режиме на диске.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL и UpdateURL  
 Ниже приведены четыре варианта URL-адрес для развертывания ClickOnce.  
  
|Параметр URL-адрес|Описание|  
|----------------|-----------------|  
|`PublishURL`|Требуется, если при публикации приложения ClickOnce на веб-сайт.|  
|`InstallURL`|Необязательный. Задайте этот параметр URL-адрес, если сайта установки отличается от `PublishURL`. Например, можно задать `PublishURL` путь FTP и набор `InstallURL` для URL-адрес.|  
|`SupportURL`|Необязательный. Задайте этот параметр URL-адрес, если на сайт службы поддержки отличается от `PublishURL`. Например, можно задать `SupportURL` для веб-сайта поддержки пользователей компании.|  
|`UpdateURL`|Необязательный. Задайте этот параметр URL-адрес, если расположение обновлений отличается от `InstallURL`. Например, можно задать `PublishURL` путь FTP и набор `UpdateURL` для URL-адрес.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



