---
title: Использование скриптов Windows PowerShell для публикации в средах разработки и тестирования | Документация Майкрософт
description: Узнайте, как с помощью сценариев Windows PowerShell из Visual Studio для публикации для разработки и тестирования сред.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002717"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Использование скриптов Windows PowerShell для публикации в тестовую среду и среду разработки

При создании веб-приложения в Visual Studio, можно создать сценарий Windows PowerShell, который можно использовать позже для автоматизации публикации веб-сайта в Azure в качестве веб-приложения в службе приложений Azure или виртуальной машине. Можно изменять и расширять скрипт Windows PowerShell в редакторе Visual Studio в соответствии с требованиями или интегрировать его с существующей сборки, тестирования и публикации скриптов.

С помощью этих скриптов, вы можете подготовить настроенные версии (также известный как среды разработки и тестирования) на узле для временного использования. Например можно настроить определенную версию веб-сайта на виртуальной машине Azure или промежуточный слот на веб-сайт для запуска набора тестов, воспроизведения ошибки, тестирования исправления ошибки, оценки предложенного изменения или настройки нестандартной среды для проведения демонстрации или презентации. Создав сценарий публикации проекта, можно воссоздать идентичные среды путем повторного запуска скрипта, при необходимости, или запустите скрипт для собственной сборки веб-приложения, чтобы создать настраиваемую среду для тестирования.

## <a name="prerequisites"></a>Предварительные требования

* Пакет Azure SDK 2.3 или более поздней версии. См. в разделе [загружаемые файлы Visual Studio](http://go.microsoft.com/fwlink/?LinkID=624384). (Не требуется пакет SDK Azure для создания сценариев для веб-проектов. Эта функция предназначена для веб-проектов, а не веб-ролей облачных служб.)
* Azure PowerShell 0.7.4 или более поздней версии. См. в разделе [описывается установка и настройка Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) или более поздней версии.

## <a name="additional-tools"></a>Дополнительные инструменты

Доступны дополнительные инструменты и ресурсы для работы с PowerShell в Visual Studio для разработки в Azure. См. в разделе [средства PowerShell для Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Создание скриптов публикации

Можно создать скрипты публикации для виртуальной машины, на котором размещена веб-сайта, при создании нового проекта, следуя [эти инструкции](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Вы также можете [создать скрипты публикации для веб-приложений в службе приложений Azure](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Скрипты, создаваемые в Visual Studio

Visual Studio создает папку уровня решения с именем **PublishScripts** , содержащий два файла Windows PowerShell, скрипт публикации для виртуальной машины или веб-сайта и модуль, который содержит функции, которые можно использовать в сценарии. Visual Studio также создает файл в формат JSON, который указывает сведения о которой выполняется развертывание проекта.

### <a name="windows-powershell-publish-script"></a>Скрипт публикации Windows PowerShell

Скрипт публикации содержит определенные действия публикации для развертывания на веб-сайта или виртуальной машины. Visual Studio предоставляет раскраску синтаксических конструкций для разработки Windows PowerShell. Справка по функции доступен, и вы можете свободно изменять функции сценария в соответствии со своими потребностями.

### <a name="windows-powershell-module"></a>Модуль Windows PowerShell

Модуль Windows PowerShell, создаваемый Visual Studio содержит функции, используемые в скрипте публикации. Эти функции Azure PowerShell не предназначены для изменяться. См. в разделе [описывается установка и настройка Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Файл конфигурации JSON

JSON-файл создается в **конфигураций** папки и содержит данные конфигурации, указывающие, какие именно ресурсы нужно развернуть в Azure. Имя файла, который Visual Studio создает проект имя WAWS-dev.json при создании веб-сайта или имя проекта-VM-dev.json при создании виртуальной машины. Ниже приведен пример файла конфигурации JSON, который создается при создании веб-сайта. Большая часть значений говорят сами за себя. Имя веб-сайта формируется Azure, в том случае, поэтому может не совпадать с именем проекта.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

При создании виртуальной машины, файл конфигурации JSON выглядит следующим образом. Облачная служба создается как контейнер для виртуальной машины. Виртуальная машина содержит обычные конечные точки для веб-доступа через HTTP и HTTPS, а также конечные точки для веб-развертывания, которая позволит публиковать на веб-сайт из вашего локального компьютера, удаленного рабочего стола и Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Можно изменить конфигурации JSON для изменения, что происходит при выполнении сценариев публикации. `cloudService` И `virtualMachine` разделы являются обязательными, но вы можете удалить `databases` раздел, если он не нужен. Пустые свойства в файле конфигурации по умолчанию, создаваемый Visual Studio являются необязательными. требуются те свойства, которые имеют значения в файле конфигурации по умолчанию.

При наличии веб-сайт с несколькими средами развертывания (также известны как слоты), а не на одном рабочем узле в Azure, можно включить имя слота, имя веб-сайта в файле конфигурации JSON. Например, если у вас есть веб-сайт с именем **mysite** а его слот называется **тестирования** то URI будет `mysite-test.cloudapp.net`, но правильное имя, используемое в файле конфигурации — mysite(test). Вы можете сделать, только если веб-сайт и слоты уже есть в вашей подписке. Если они не существуют, создайте веб-сайт, запустив сценарий без указания слота, затем создайте слот на [портала Azure](https://portal.azure.com/), и запустите скрипт с именем измененного веб-сайта. Дополнительные сведения о слотах развертывания для веб-приложений см. в разделе [Настройка промежуточных сред для веб-приложений в службе приложений Azure](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Запуск скриптов публикации

Если вы ранее не работали перед сценарий Windows PowerShell, сначала необходимо задать политику выполнения, чтобы включить выполнение сценариев. Политика — это функция безопасности, чтобы запретить пользователям запускать скрипты Windows PowerShell, если они уязвимы для вредоносного по или вирусов, связанные с выполнением скриптов.

### <a name="run-the-script"></a>Запустите сценарий

1. Создание пакета веб-развертывания для проекта. Пакет веб-развертывания представляет собой сжатый архив (ZIP-файл) с файлами, которые требуется скопировать на веб-сайта или виртуальной машины. Пакеты веб-развертывания в Visual Studio можно создать для любого веб-приложения.

   ![Создание веб-развертывание пакета](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Дополнительные сведения см. в разделе [как: Создание веб-пакета развертывания в Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Также вы можете автоматизировать создание пакета веб-развертывания, как описано в разделе [Настройка и расширение сценариев публикации](#customizing-and-extending-publish-scripts).

1. В **обозревателе решений**, откройте контекстное меню для сценария и выберите **открыть с помощью PowerShell ISE**.
1. Если выполнение сценариев Windows PowerShell на этом компьютере впервые, откройте окно командной строки с правами администратора и введите следующую команду:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Войдите в Azure с помощью следующей команды.

    ```powershell
    Add-AzureAccount
    ```

    Ответ на запрос введите имя пользователя и пароль.

    Обратите внимание, что после автоматизации работы сценария этот способ указания учетных данных Azure не работать. Вместо этого следует использовать `.publishsettings` файл для предоставления учетных данных. Один раз, можно использовать только команды **Get-AzurePublishSettingsFile** чтобы скачать файл из Azure, а впоследствии используете **Import-AzurePublishSettingsFile** для импорта файла. Подробные инструкции см. в разделе [описывается установка и настройка Azure PowerShell](/powershell/azure/overview).

1. (Необязательно) Если вы хотите создать ресурсы Azure, например виртуальная машина, веб-сайт, не публикуя веб-приложения и базы данных используйте **Publish-WebApplication.ps1** с **-конфигурации**аргумент задан в файле конфигурации JSON. Эта командная строка использует файл конфигурации JSON, чтобы определить, какие именно ресурсы нужно создать. Так как оно использует параметры по умолчанию для других аргументов командной строки, он создает ресурсы, но недостаточно для публикации веб-приложения. -Verbose параметр предоставляет дополнительные сведения о том, что происходит.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Используйте **Publish-WebApplication.ps1** команды, как показано в одном из следующих примеров, чтобы вызвать скрипт и опубликовать веб-приложения. Если вам нужно переопределить параметры по умолчанию для любых других аргументов, например имя подписки, опубликовать имя пакета, учетные данные виртуальной машины или учетные данные сервера базы данных, можно указать эти параметры. Используйте **– Verbose** параметр, чтобы просмотреть дополнительные сведения о ходе выполнения процесса публикации.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Если вы создаете виртуальную машину, команда выглядит следующим образом. В этом примере также показано, как указать учетные данные для нескольких баз данных. Для виртуальных машин, создаваемых этими сценариями SSL-сертификат не из доверенного корневого центра. Таким образом, необходимо использовать **– AllowUntrusted** параметр.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Скрипт может создавать базы данных, но он не создает серверов баз данных. Если вы хотите создать сервер базы данных, можно использовать **New-AzureSqlDatabaseServer** функции в модуле Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Настройка и расширение сценариев публикации

Можно настроить сценарии публикации и файл конфигурации JSON. Функции в модуле Windows PowerShell **AzureWebAppPublishModule.psm1** не должна изменяться. Если вам нужно просто указать другую базу данных или изменить некоторые свойства виртуальной машины, измените файл конфигурации JSON. Если вы хотите расширить функциональные возможности скрипта для автоматизации сборки и тестирования своего проекта, можно реализовать заглушки функций в **Publish-WebApplication.ps1**.

Чтобы автоматизировать сборку проекта, добавьте код, вызывающий функцию MSBuild `New-WebDeployPackage` так, как показано в следующем примере кода. Путь к команде MSBuild отличается в зависимости от версии Visual Studio, вы установили. Чтобы получить правильный путь, можно использовать функцию **Get-MSBuildCmd**, как показано в следующем примере.

### <a name="to-automate-building-your-project"></a>Чтобы автоматизировать сборку проекта

1. Добавление `$ProjectFile` параметр в раздел глобальных параметров.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Скопируйте функцию `Get-MSBuildCmd` в свой файл сценария.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Замените `New-WebDeployPackage` со следующим кодом и замените заполнители в строке `$msbuildCmd`. Этот код предназначен для Visual Studio 2015. Если вы используете Visual Studio 2017, измените **VisualStudioVersion** свойства `15.0` (`12.0` для Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Для создания веб-приложения, используйте MsBuild.exe. Получить справку см. в разделе Справочник по командной строке MSBuild в: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Запуск выполнения команды сборки

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Вызовите `New-WebDeployPackage` функции перед этой строкой: `$Config = Read-ConfigFile $Configuration` для веб-приложений или `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` для виртуальных машин.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Вызовите настроенный сценарий из командной строки, передав `$Project` аргумент, как показано в следующем примере:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Чтобы автоматизировать тестирование приложения, добавьте код для `Test-WebApplication`. Обязательно раскомментируйте в **Publish-WebApplication.ps1** где вызываются эти функции. Если реализация не предоставлена, можно вручную построить проект с помощью Visual Studio и запустите скрипт публикации для публикации в Azure.

## <a name="publishing-function-summary"></a>Обзор функций публикации
Чтобы получить справку для функции, которые можно использовать в командной строке Windows PowerShell, используйте команду `Get-Help function-name`. Справка содержит параметров и примеры их использования. Один и тот же текст справки также находится в исходных файлах сценариев **AzureWebAppPublishModule.psm1** и **Publish-WebApplication.ps1**. Сценарий и Справка переведены на язык Visual Studio.

**AzureWebAppPublishModule**

| Имя функции | Описание |
| --- | --- |
| Add-AzureSQLDatabase |Создает новую базу данных Azure SQL. |
| Add-AzureSQLDatabases |Создает базы данных Azure SQL от значений в файле конфигурации JSON, который создается в Visual Studio. |
| Add-AzureVM |Создает виртуальную машину Azure и возвращает URL-адрес развернутой виртуальной машины. Эта функция настраивает обязательные компоненты и затем вызывает **New-AzureVM** (модуль Azure) для создания новой виртуальной машины. |
| Add-AzureVMEndpoints |Добавляет новые входные конечные точки виртуальной машины и возвращает виртуальную машину с новой конечной точки. |
| Add-AzureVMStorage |Создает новую учетную запись хранения Azure в текущей подписке. Имя учетной записи начинается с devtest, уникальный буквенно-цифровой строкой. Функция возвращает имя учетной записи хранения. Укажите расположение или территориальную группу для новой учетной записи хранения. |
| Add-AzureWebsite |Создает веб-сайт с указанным именем и расположением. Эта функция вызывает **New-AzureWebsite** функции в модуле Azure. Если в подписке еще нет веб-сайт с указанным именем, эта функция создает веб-сайт и возвращает объект веб-сайта. В противном случае возвращает значение `$null`. |
| BACKUP-Subscription |Сохраняет текущую подписку Azure в `$Script:originalSubscription` переменной в области сценария. Эта функция сохраняет текущую подписку Azure (полученную с помощью `Get-AzureSubscription -Current`) и ее учетную запись хранения, а также подписку, которую изменяет этот сценарий (хранится в переменной `$UserSpecifiedSubscription`) и ее учетную запись хранения, в области сценария. Сохранив эти значения, можно использовать функции, такие как `Restore-Subscription`для восстановления исходной текущей подписки и учетной записи хранения в актуальное состояние, если текущее состояние изменилось. |
| Find-AzureVM |Возвращает указанную виртуальную машину Azure. |
| Format-DevTestMessageWithTime |Добавляет в начало даты и времени в сообщение. Эта функция предназначена для сообщений, записываемых в потоки Error и Verbose. |
| Get-AzureSQLDatabaseConnectionString |Собирает строку подключения для подключения к базе данных Azure SQL. |
| Get-AzureVMStorage |Возвращает имя первой учетной записи хранения с шаблоном имени «devtest *"(без учета регистра) в указанном расположении или территориальной группе. Если «devtest*"учетная запись хранения не соответствует расположению или территориальной группе, функция пропускает ее. Укажите расположение или территориальную группу. |
| Get-MSDeployCmd |Возвращает команду для запуска средства MsDeploy.exe. |
| New-AzureVMEnvironment |Находит или создает виртуальную машину в подписке, которая соответствует значениям в файле конфигурации JSON. |
| Publish-WebPackage |Использует MsDeploy.exe и веб-публикация пакета. ZIP-файл для развертывания ресурсов на веб-сайт. Эта функция не создает никаких выходных данных. Если вызов MSDeploy.exe завершается ошибкой, функция создает исключение. Чтобы получить более подробные выходные данные, используйте **-Verbose** параметр. |
| Publish-WebPackageToVM |Проверяет значения параметров, а затем вызывает **Publish-WebPackage** функции. |
| Read-ConfigFile |Проверяет файл конфигурации JSON и возвращает хэш-таблицу выбранных значений. |
| RESTORE-Subscription |Сбрасывает текущую подписку для исходной подписки. |
| Test-AzureModule |Возвращает `$true` Если установлен модуль Azure версии 0.7.4 или более поздней версии. Возвращает `$false` Если модуль не установлен или имеет более ранней версии. Эта функция не имеет параметров. |
| AzureModuleVersion теста |Возвращает `$true` Если версия модуля Azure 0.7.4 или более поздней версии. Возвращает `$false` Если модуль не установлен или имеет более ранней версии. Эта функция не имеет параметров. |
| HttpsUrl теста |Преобразует входной URL-адрес в объект System.Uri. Возвращает `$True` Если URL-адрес является абсолютным адресом и использует схему https. Возвращает `$false` Если URL-адрес является относительным, не использует схему HTTPS или входную строку невозможно преобразовать в URL-адрес. |
| Элемент теста |Возвращает `$true` Если свойство или метод является членом объекта. В противном случае возвращает значение `$false`. |
| ErrorWithTime записи |Записывает сообщение об ошибке с префиксом с текущим временем. Эта функция вызывает **Format-DevTestMessageWithTime** функции, чтобы добавить время перед записью сообщения в поток ошибок. |
| HostWithTime записи |Записывает сообщение в основную программу (**Write-Host**) с префиксом с текущим временем. Результат записи в основную программу варьируется. Большинство программ, на которых размещены Windows PowerShell, записывают эти сообщения в стандартный вывод. |
| VerboseWithTime записи |Записывает подробное сообщение с префиксом с текущим временем. Так как он вызывает **Write-Verbose**, сообщение отображается только при запуске сценария с **Verbose** параметр или если **VerbosePreference** параметра  **По-прежнему**. |

**Публикация — веб-приложения**

| Имя функции | Описание |
| --- | --- |
| Новый AzureWebApplicationEnvironment |Создает ресурсы Azure, таких как веб-сайта или виртуальной машины. |
| Новый WebDeployPackage |Эта функция не реализована. Можно добавить команды в этой функции для построения проекта. |
| Публикация AzureWebApplication |Публикует веб-приложения в Azure. |
| Публикация — веб-приложения |Создает и развертывает веб-приложений, виртуальных машин, баз данных SQL и учетные записи хранения для веб-проекта Visual Studio. |
| Тест-веб-приложения |Эта функция не реализована. Можно добавить команды в этой функции для тестирования приложения. |

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о сценариях PowerShell, считывая [работа со сценариями Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) и другими сценариями Azure PowerShell см. в разделе [Script Center](https://azure.microsoft.com/documentation/scripts/).
