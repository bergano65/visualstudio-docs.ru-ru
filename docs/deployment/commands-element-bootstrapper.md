---
title: "&lt;Команды&gt; элемент (загрузчик) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 67bbb7cbec1df53a8481acf26273cc371f92bb40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Команды&gt; элемент (загрузчик)
`Commands` Элемент реализует тесты, которые описываются элементами, расположенными под `InstallChecks` элемент и объявляет пакет, который [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] загрузчик должен установить в случае сбоя проверки.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `Commands` Элемент является обязательным. Элемент имеет следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Reboot`|Необязательный. Определяет, следует ли перезапуска системы, если какие-либо пакеты возвращать код завершения перезагрузки. Ниже перечислены допустимые значения:<br /><br /> `Defer`. Перезагрузка откладывается до некоторого момента в будущем.<br /><br /> `Immediate`. Вызывает немедленную перезагрузку, если один из пакетов вернула код завершения перезагрузки.<br /><br /> `None`. В результате все запросы перезапуска пропускаются.<br /><br /> Значение по умолчанию — `Immediate`.|  
  
## <a name="command"></a>Команда  
 Элемент `Command` является дочерним для элемента `Commands`. Объект `Commands` элемент может иметь один или несколько `Command` элементов. Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`PackageFile`|Обязательно. Имя пакета для установки следует один или несколько условий, заданных элементом `InstallConditions` возвращают значение false. Пакет должен определяться в одном файле с помощью `PackageFile` элемента.|  
|`Arguments`|Необязательный. Набор аргументов командной строки для передачи в файле пакета.|  
|`EstimatedInstallSeconds`|Необязательный. Предполагаемое время в секундах, необходимое для установки пакета. Это значение определяет размер индикатора выполнения, отображаемого загрузчиком для пользователя. Значение по умолчанию — 0, в этом случае времени не указан оценки.|  
|`EstimatedDiskBytes`|Необязательный. Предполагаемый объем места на диске, в байтах, которое займет пакет после установки завершено. Это значение используется в требования к дисковому пространству, отображаемых загрузчиком для пользователя. Значение по умолчанию — 0, в котором случае загрузчик не отображает все требования к месту на жестком диске.|  
|`EstimatedTempBytes`|Необязательный. Предполагаемый размер временного места на диске, в байтах, который потребуется для пакета.|  
|`Log`|Необязательный. Путь к файлу журнала, который создает пакет относительно корневого каталога пакета.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Элемент является дочерним элементом `Command` элемента. Каждый `Command` элемент может иметь не более одного `InstallConditions` элемента. Если не `InstallConditions` элемент существует, пакет, указанный параметром `Condition` всегда будет работать.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Элемент является дочерним элементом `InstallConditions` элемент и описывает положительное условие, при котором команда не должна выполняться. Каждый `InstallConditions` элемент может иметь ноль или более `BypassIf` элементов.  
  
 `BypassIf`имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Property`|Обязательно. Имя свойства для тестирования. Свойство необходимо предварительно определено потомком элемента `InstallChecks` элемент. Дополнительные сведения см. в разделе [ \<InstallChecks > элемент](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательно. Тип выполняемого сравнения. Ниже перечислены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательно. Значение, сравниваемое со свойством.|  
|`Schedule`|Необязательный. Имя `Schedule` тег, который определяет, когда следует применять это правило.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Элемент является дочерним элементом `InstallConditions` элемент и описывает положительное условие, в котором следует остановить процесс установки. Каждый `InstallConditions` элемент может иметь ноль или более `FailIf` элементов.  
  
 `FailIf`имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Property`|Обязательно. Имя свойства для тестирования. Свойство необходимо предварительно определено потомком элемента `InstallChecks` элемент. Дополнительные сведения см. в разделе [ \<InstallChecks > элемент](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательно. Тип выполняемого сравнения. Ниже перечислены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательно. Значение, сравниваемое со свойством.|  
|`String`|Необязательный. Текст, отображаемый для пользователя при сбое.|  
|`Schedule`|Необязательный. Имя `Schedule` тег, который определяет, когда следует применять это правило.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Элемент является дочерним элементом `Command` элемента. `ExitCodes` Элемент содержит один или несколько `ExitCode` элементы, определяющие, что делать в ответ на код выхода из пакета установки. Может быть один необязательный `ExitCode` под элементом `Command` элемента. `ExitCodes`не имеет атрибутов.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode` Элемент является дочерним элементом `ExitCodes` элемента. `ExitCode` Определяет, что делать в ответ на код выхода из пакета установки. `ExitCode`не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Value`|Обязательно. Значение кода выхода, к которому `ExitCode` относится элемент.|  
|`Result`|Обязательно. Способ установки должен реагировать на данный код выхода. Ниже перечислены допустимые значения:<br /><br /> `Success`. Пакет помечается как успешно установленный.<br /><br /> `SuccessReboot`. Пакет помечается как успешно установленный и указывает, что перезагрузки системы.<br /><br /> `Fail`. Пакет помечается как ошибка.<br /><br /> `FailReboot`. Пакет помечается как сбой и предписывает перезагрузки системы.|  
|`String`|Необязательный. Значение, отображаемое для пользователя в ответ на данный код выхода.|  
|`FormatMessageFromSystem`|Необязательный. Определяет, следует ли использовать системные ошибки сообщение, соответствующее коду выхода, или значение, указанное в `String`. Допустимые значения: `true`, что означает использование системных ошибок и `false`, означающее использовать строку, предоставляемые `String`. Значение по умолчанию — `false`. Если это свойство имеет `false`, но `String` не задано, будет использоваться системные ошибки.|  
  
## <a name="example"></a>Пример  
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
  
## <a name="see-also"></a>См. также  
 [Продукт и справочник по схемам пакета](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > элемент](../deployment/installchecks-element-bootstrapper.md)