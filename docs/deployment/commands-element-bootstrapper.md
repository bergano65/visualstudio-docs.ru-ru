---
title: "Элемент &lt;Commands&gt; (загрузчик) | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Commands> - элемент [загрузчик]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;Commands&gt; (загрузчик)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент `Commands` реализует тесты, которые описываются элементами, расположенными под элементом `InstallChecks`, и объявляет пакет, который должен устанавливаться загрузчиком [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] при неудачном завершении тестов.  
  
## Синтаксис  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## Элементы и атрибуты  
 Элемент `Commands` является обязательным.  Он имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Reboot`|Необязательный.  Определяет, следует ли производить перезагрузку системы, если какие\-либо из пакетов возвратят код выхода, указывающий на необходимость перезагрузки.  Допустимые значения приведены в следующем списке:<br /><br /> `Defer`.  Перезагрузка откладывается до некоторого момента в будущем.<br /><br /> `Immediate`.  Вызывает немедленную перезагрузку, если один из пакетов возвращает код выхода, указывающий на необходимость перезагрузки.<br /><br /> `None` Запросы на перезагрузку игнорируются.<br /><br /> По умолчанию используется значение `Immediate`.|  
  
## Command  
 Элемент `Command` является дочерним для элемента `Commands`.  В элементе `Commands` может содержаться как минимум один элемент `Command` .  Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`PackageFile`|Обязательный.  Имя пакета, который следует установить в случае, если одно или несколько условий, заданных элементом `InstallConditions`, возвратят значение false.  Пакет должен быть определен в том же файле с использованием элемента `PackageFile`.|  
|`Arguments`|Необязательный.  Набор аргументов командной строки для передачи файлу пакета.|  
|`EstimatedInstallSeconds`|Необязательный.  Оценка времени в секундах, которое займет установка пакета.  Это значение определяет размер индикатора выполнения, отображаемого загрузчиком для пользователя.  По умолчанию этот атрибут имеет значение 0, т. е. оценка времени не дается.|  
|`EstimatedDiskBytes`|Необязательный.  Оценка объема дискового пространства в байтах, которое займет пакет по завершении установки.  Это значение указывается в требованиях к дисковому пространству, отображаемых загрузчиком для пользователя.  По умолчанию задано значение 0, т. е. загрузчик не отображает требования к дисковому пространству.|  
|`EstimatedTempBytes`|Необязательный.  Оценка объема временного дискового пространства в байтах, которое потребуется для пакета.|  
|`Log`|Необязательный.  Путь к генерируемому пакетом файлу журнала, заданный относительно корневого каталога пакета.|  
  
## InstallConditions  
 Элемент `InstallConditions` является дочерним для элемента `Command`.  Каждый элемент `Command` может содержать не более одного элемента `InstallConditions`.  Если элемент `InstallConditions` не существует, пакет, заданный атрибутом `Condition`, будет всегда запускаться.  
  
## BypassIf  
 Элемент `BypassIf` является дочерним для элемента `InstallConditions` и описывает положительное условие, при котором команда не должна выполняться.  В каждом элементе `InstallConditions` может содержаться любое число элементов `BypassIf`, включая ноль.  
  
 `BypassIf` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Property`|Обязательный.  Задает имя тестируемого свойства.  Свойство должно быть предварительно определено потомком элемента `InstallChecks`.  Дополнительные сведения см. в разделе [Элемент \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательный.  Тип выполняемого сравнения.  Допустимые значения приведены в следующем списке:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательный.  Значение, с которым будет сравниваться свойство.|  
|`Schedule`|Необязательный.  Имя тега `Schedule`, определяющего, когда следует применять данное правило.|  
  
## FailIf  
 Элемент `FailIf` является дочерним для элемента `InstallConditions` и описывает положительное условие, при котором следует остановить процесс установки.  В каждом элементе `InstallConditions` может содержаться любое число элементов `FailIf`, включая ноль.  
  
 `FailIf` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Property`|Обязательный.  Задает имя тестируемого свойства.  Свойство должно быть предварительно определено потомком элемента `InstallChecks`.  Дополнительные сведения см. в разделе [Элемент \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательный.  Тип выполняемого сравнения.  Допустимые значения приведены в следующем списке:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательный.  Значение, с которым будет сравниваться свойство.|  
|`String`|Необязательный.  Текст, отображаемый для пользователя при отрицательном результате теста.|  
|`Schedule`|Необязательный.  Имя тега `Schedule`, определяющего, когда следует применять данное правило.|  
  
## ExitCodes  
 Элемент `ExitCodes` является дочерним для элемента `Command`.  Элемент `ExitCodes` содержит один или более элементов `ExitCode`, определяющих действия, выполняемые в процессе установки в ответ на возвращенный пакетом код выхода.  Под элементом `Command` может быть один необязательный элемент `ExitCode`.  Элемент `ExitCodes` не имеет атрибутов.  
  
## ExitCode  
 Элемент `ExitCode` является дочерним для элемента `ExitCodes`.  Элемент `ExitCode` определяет действия, выполняемые в процессе установки в ответ на возвращенный пакетом код выхода.  Элемент `ExitCode` не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Value`|Обязательный.  Значение кода выхода, к которому относится данный элемент `ExitCode`.|  
|`Result`|Обязательный.  Способ реагирования на данный код выхода в процессе установки.  Допустимые значения приведены в следующем списке:<br /><br /> `Success`.  Пакет помечается как успешно установленный.<br /><br /> `SuccessReboot`.  Пакет помечается как успешно установленный, а системе дается команда на перезагрузку.<br /><br /> `Fail`.  Пакет помечается как вызвавший сбой.<br /><br /> `FailReboot`.  Пакет помечается как вызвавший сбой, а системе дается команда на перезагрузку.|  
|`String`|Необязательный.  Значение, которое должно быть отображено для пользователя в ответ на данный код выхода.|  
|`FormatMessageFromSystem`|Необязательный.  Определяет, следует ли использовать системное сообщение об ошибке, соответствующее коду выхода, или же значение, указанное в атрибуте `String`.  Допустимые значения – `true` \(используется системное сообщение об ошибке\) и `false` \(используется строка, указанная в атрибуте `String`\).  Значение по умолчанию — `false`.  Если это свойство имеет значение `false`, но атрибут `String` не установлен, будет использоваться системное сообщение об ошибке.|  
  
## Пример  
 В следующем примере кода определяются команды для установки .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)   
 [Элемент \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md)