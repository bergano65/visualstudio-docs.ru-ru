---
title: "Построение ClickOnce-приложений из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "развертывание ClickOnce, из командной строки"
  - "публикация"
  - "публикация, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Построение ClickOnce-приложений из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] можно построить проекты из командной строки, даже если они созданы в интегрированной среде разработки \(IDE\).  На самом деле можно перестроить проект, созданный при помощи [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], на другом компьютере, имеющем только установленный [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Это позволяет повторно создать построение при помощи автоматизированного процесса, например в центральной лаборатории построения, или используя дополнительные методы написания сценариев вне области построения самого проекта.  
  
## Использование MSBuild для повторного развертывания ClickOnce\-приложений  
 При вызове в командной строке команды msbuild \/target:publish она указывает системе MSBuild на необходимость построения проекта и создания приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] в папке публикации.  Это эквивалентно выбору команды **Публиковать** в IDE.  
  
 Эта команда запускает файл msbuild.exe, путь к которому находится в среде командной строки Visual Studio.  
  
 "Целевым объектом" является индикатор для MSBuild того, как обработать команду.  Ключевыми целевыми объектами является целевой объект "построение" и целевой объект "публикация".  Целевой объект построения является эквивалентом выбору команды построения \(или нажатию клавиши F5\) в IDE.  Если необходимо только построить проект, для этого можно ввести `msbuild`.  Эта команда работает, поскольку целевой объект построения является целевым объектом по умолчанию для всех проектов, которые создает [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Это означает, что не нужно указывать явно целевой объект построения.  Таким образом, `msbuild` работает аналогично команде `msbuild /target:build`.  
  
 При выполнении команды `/target:publish` MSBuild вызывает целевой объект публикации.  Целевой объект публикации зависит от целевого объекта построения.  Это означает, что операция публикации является надмножеством операции построения.  Например, если выполняется изменение в одном из исходных файлов Visual Basic или C\#, операцией публикации автоматически выполняется перестройка соответствующего построения.  
  
 Сведения о формировании полного развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] с использованием средства командной строки Mage.exe для создания манифеста [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] см. в разделе [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Создание и построение базового ClickOnce\-приложения при помощи MSBuild  
  
#### Создание и публикация проекта ClickOnce  
  
1.  В меню **Файл** выберите команду **Создать проект**.  Откроется диалоговое окно **Новый проект**.  
  
2.  Выберите **Приложение Windows** и назовите его `CmdLineDemo`.  
  
3.  В меню **Построение** выберите команду **Публикация**.  
  
     Этот шаг обеспечивает правильную настройку проекта для формирования развертывания приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
     Откроется мастер публикации.  
  
4.  В мастере публикации нажмите кнопку **Готово**.  
  
     Visual Studio создает и отображает веб\-страницу по умолчанию с именем Publish.htm.  
  
5.  Сохраните проект и запомните местоположение папки, в которой он сохранен.  
  
 Вышеприведенные шаги создают проект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], опубликованный в первый раз.  Теперь можно воспроизвести построение вне IDE.  
  
#### Воспроизведение построения из командной строки  
  
1.  Выйдите из [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  В меню Windows **Пуск** последовательно выберите **Все программы**, **Microsoft Visual Studio**, **Средства Visual Studio**, **Командная строка Visual Studio**.  В результате должна открыться командная строка в корневой папке текущего пользователя.  
  
3.  В **командной строке Visual Studio** измените текущий каталог на местоположение только что построенного проекта.  Например, введите `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Чтобы удалить существующие файлы, созданные в разделе "Создание и публикация проекта [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]", введите `rmdir /s publish`.  
  
     Этот шаг не является обязательным, но он обеспечивает создание всех новых файлов построения с использованием командной строки.  
  
5.  Введите `msbuild /target:publish`.  
  
 Вышеприведенные шаги создадут полное развертывание приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] во вложенной папке проекта с именем **Publish**.  CmdLineDemo.application является манифестом развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Папка CmdLineDemo\_1.0.0.0 содержит файлы CmdLineDemo.exe и CmdLineDemo.exe.manifest, манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Setup.exe является загрузчиком, который по умолчанию настроен на установку [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Папка DotNetFX содержит распространяемые модули для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Это весь полный набор файлов, необходимых для развертывания приложения через Интернет либо через UNC\-папку или компакт\-диски и диски DVD.  
  
## Свойства публикации  
 При публикации приложения в вышеуказанных процедурах мастер публикации вставляет в файл проекта следующие свойства.  Эти свойства непосредственно влияют на то, как создается приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 В CmdLineDemo.vbproj \/ CmdLineDemo.csproj:  
  
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
  
 Можно переопределить эти свойства в командной строке, не изменяя сам файл проекта.  Например, следующая команда выполняет построение развертывания приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] без загрузчика:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Свойства публикации контролируются в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из страниц свойств **Публикация**, **Безопасность** и **Подпись** в **конструкторе проектов**.  Далее приводится описание свойств публикации наряду с тем, как каждое из этих свойств устанавливается на разных страницах свойств конструктора приложений.  
  
-   `AssemblyOriginatorKeyFile` определяет файл ключей, используемый для подписи манифестов приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Тот же ключ может также использоваться для назначения строгих имен сборок.  Это свойство устанавливается на странице **Подпись** в **конструкторе проектов**.  
  
 Следующие свойства устанавливаются на странице **Безопасность**:  
  
-   **Включить параметры безопасности ClickOnce\-приложений** — определяет, будут ли создаваться манифесты [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  При начальном создании проекта генерирование манифеста [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] по умолчанию отключено.  Мастер автоматически устанавливает этот флаг при публикации в первый раз.  
  
-   **TargetZone** — определяет уровень доверия, передаваемый в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Возможными значениями являются "Internet", "LocalIntranet" и "Custom".  "Интернет" и "Локальная интрасеть" определяют, что в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] предоставляется набор разрешений по умолчанию.  LocalIntranet является значением по умолчанию и по существу означает полное доверие.  "Настраиваемая" указывает, что только разрешения, явно задаваемые в файле app.manifest, должны предоставляться в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Файл app.manifest является файлом частичного манифеста, содержащим лишь определения сведений о доверии.  Это скрытый файл, автоматически добавляемый в проект при настройке разрешений на странице **Безопасность**.  
  
 Следующие свойства устанавливаются на странице **Публикация**.  
  
-   `PublishUrl` является местом, куда приложение будет публиковаться в среде IDE.  Оно вставляется в манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], если не указано свойство `InstallUrl` или `UpdateUrl`.  
  
-   `ApplicationVersion` задает версию приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Это номер версии из четырех цифр.  Если вместо последней цифры стоит символ "\*", тогда `ApplicationRevision` заменяется значением, вставленным в манифест во время построения.  
  
-   `ApplicationRevision` задает редакцию.  Это целое число, которое увеличивается при каждой публикации в IDE.  Следует отметить, что оно не увеличивается автоматически для построний, выполненных в командной строке.  
  
-   `Install` определяет, является ли приложение установленным приложением или приложением, выполняющимся из Интернета.  
  
-   `InstallUrl` \(не показано\) является местоположением, из которого пользователи будут выполнять установку приложения.  Если это значение задано, оно записывается в загрузчик setup.exe, при условии что включено свойство `IsWebBootstrapper`.  Оно также вставляется в манифест приложения, если не указано свойство `UpdateUrl`.  
  
-   `SupportUrl` \(не показано\) является местоположением, на которое имеется ссылка в диалоговом окне **Установка и удаление программ** для установленного приложения.  
  
 Следующие свойства установлены в диалоговом окне **Обновления приложения**, которое можно открыть со страницы **Публикация**.  
  
-   `UpdateEnabled` указывает, должно ли приложение проверять наличие обновлений.  
  
-   `UpdateMode` указывает, выполняются обновления с высоким приоритетом или в фоновом режиме.  
  
-   `UpdateInterval` указывает, как часто приложение должно выполнять проверку наличия обновлений.  
  
-   `UpdateIntervalUnits` указывает, задается значение `UpdateInterval` в часах, днях или в неделях.  
  
-   `UpdateUrl` \(не показано\) является местоположением, из которого приложение будет получать обновления.  Если это значение задано, оно вставляется в манифест приложения.  
  
-   Следующие свойства установлены в диалоговом окне **Параметры публикации**, которое можно открыть со страницы **Публикация**.  
  
-   `PublisherName` указывает имя издателя, отображаемое в командной строке при установке или выполнении приложения.  В случае установленного приложения оно также используется для указания имени папки в меню **Пуск**.  
  
-   `ProductName` указывает имя продукта, отображаемое в командной строке при установке или выполнении приложения.  В случае установленного приложения оно также используется для указания ярлыка в меню **Пуск**.  
  
-   Следующие свойства установлены в диалоговом окне **Необходимые компоненты**, которое можно открыть со страницы **Публикация**.  
  
-   `BootstrapperEnabled` определяет, создавать ли загрузчик setup.exe.  
  
-   `IsWebBootstrapper` определяет, работает загрузчик setup.exe через Интернет или в режиме, основанном на обращении к диску.  
  
## InstallURL, SupportUrl, PublishURL и UpdateURL  
 В следующей таблице показано четыре параметра URL\-адреса для развертывания с помощью ClickOnce.  
  
|Параметр URL\-адреса|Описание|  
|--------------------------|--------------|  
|`PublishURL`|Требуется при публикации приложения ClickOnce на веб\-сайте.|  
|`InstallURL`|Необязательный.  Задайте этот параметр URL\-адреса, если адрес сайта установки отличается от `PublishURL`.  Например, можно было бы установить для свойства `PublishURL` путь к FTP\-серверу, а для `InstallURL` — URL\-адрес в Интернете.|  
|`SupportURL`|Необязательный.  Задайте этот параметр URL\-адреса, если адрес сайта поддержки отличается от `PublishURL`.  Например, можно задать `SupportURL` в качестве веб\-сайта поддержки пользователей своей компании.|  
|`UpdateURL`|Необязательный.  Задайте этот параметр URL\-адреса, если расположение обновлений отличается от `InstallURL`.  Например, можно было бы установить для свойства `PublishURL` путь к FTP\-серверу, а для `UpdateURL` — URL\-адрес в Интернете.|  
  
## См. также  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)