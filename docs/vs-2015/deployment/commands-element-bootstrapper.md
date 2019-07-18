---
title: '&lt;Команды&gt; элемент (загрузчик) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205345"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Команды&gt; элемент (установщик)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Commands` Элемент реализует тесты, описываемого элементов, расположенных под `InstallChecks` элемент и объявляет пакет, который [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] загрузчик должен установить, если тест не пройден.  
  
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
 `Commands` Элемент является обязательным. Элемент имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Reboot`|Необязательный параметр. Определяет, следует ли перезапуска системы, если любой из пакетов возвращает код выхода перезапуска. Ниже перечислены допустимые значения:<br /><br /> `Defer`. Перезапуск откладывается до некоторого момента в будущем.<br /><br /> `Immediate`. Вызывает немедленную перезагрузку, если один из пакетов вернул код выхода перезапуска.<br /><br /> `None`. В результате любые запросы перезапуска пропускаются.<br /><br /> Значение по умолчанию — `Immediate`.|  
  
## <a name="command"></a>Command  
 Элемент `Command` является дочерним для элемента `Commands`. Объект `Commands` элемент может иметь один или несколько `Command` элементов. Элемент имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`PackageFile`|Обязательный. Имя устанавливаемого пакета следует один или несколько условий, заданных с `InstallConditions` возвращает значение false. Пакет должен быть определен в одном файле с помощью `PackageFile` элемент.|  
|`Arguments`|Необязательный параметр. Набор аргументов командной строки для передачи в файле пакета.|  
|`EstimatedInstallSeconds`|Необязательный параметр. Предполагаемое время в секундах, необходимое для установки пакета. Это значение определяет размер индикатора хода выполнения, на которые загрузчиком для пользователя. Значение по умолчанию равно 0, в этом случае времени не указан оценки.|  
|`EstimatedDiskBytes`|Необязательный параметр. Оценочный объем места на диске в байтах, которые после установки займет пакет завершения. Это значение используется в требования к дисковому пространству, загрузчиком для пользователя. Значение по умолчанию равно 0, в котором регистр загрузчик не отображает все требования к дисковому пространству.|  
|`EstimatedTempBytes`|Необязательный параметр. Предполагаемый объем временного места на диске, в байтах, который потребуется для пакета.|  
|`Log`|Необязательный параметр. Путь к файлу журнала, который создает пакет, относительно корневого каталога пакета.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Элемент является дочерним элементом `Command` элемент. Каждый `Command` элемент может иметь не более одного `InstallConditions` элемент. Если не `InstallConditions` элемент существует, пакет, указанный параметром `Condition` всегда будет работать.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Элемент является дочерним элементом `InstallConditions` элемент и описывает положительное условие, при котором команда не должна выполняться. Каждый `InstallConditions` элемент может иметь ноль или более `BypassIf` элементов.  
  
 `BypassIf` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Property`|Обязательный. Имя свойства для тестирования. Свойство необходимо предварительно определено потомком элемента `InstallChecks` элемент. Дополнительные сведения см. в разделе [ \<InstallChecks > элемент](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательный. Тип выполняемого сравнения. Ниже перечислены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательный. Значение, сравниваемое со свойством.|  
|`Schedule`|Необязательный параметр. Имя `Schedule` тег, который определяет, когда следует применять это правило.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Элемент является дочерним элементом `InstallConditions` элемент и описывает положительное условие, при котором следует остановить установку. Каждый `InstallConditions` элемент может иметь ноль или более `FailIf` элементов.  
  
 `FailIf` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Property`|Обязательный. Имя свойства для тестирования. Свойство необходимо предварительно определено потомком элемента `InstallChecks` элемент. Дополнительные сведения см. в разделе [ \<InstallChecks > элемент](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Обязательный. Тип выполняемого сравнения. Ниже перечислены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Обязательный. Значение, сравниваемое со свойством.|  
|`String`|Необязательный параметр. Текст, отображаемый для пользователя в случае сбоя.|  
|`Schedule`|Необязательный параметр. Имя `Schedule` тег, который определяет, когда следует применять это правило.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Элемент является дочерним элементом `Command` элемент. `ExitCodes` Содержит один или несколько `ExitCode` элементы, определяющие, что делать в ответ на код выхода из пакета установки. Может существовать один необязательный `ExitCode` под элементом `Command` элемент. `ExitCodes` не имеет атрибутов.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode` Элемент является дочерним элементом `ExitCodes` элемент. `ExitCode` Определяет, что делать в ответ на код выхода из пакета установки. `ExitCode` не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Value`|Обязательный. Значение кода выхода, к которому `ExitCode` относится элемент.|  
|`Result`|Обязательный. Способ установки должен реагировать на этот код выхода. Ниже перечислены допустимые значения:<br /><br /> `Success`. Пакет помечается как успешно установленный.<br /><br /> `SuccessReboot`. Пакет помечается как успешно установленный и указывает, что к перезапуску системы.<br /><br /> `Fail`. Пакет помечается как не удалось.<br /><br /> `FailReboot`. Пакет помечается как не удалось и указывает, что к перезапуску системы.|  
|`String`|Необязательный параметр. Значение, отображаемое для пользователя в ответ на этот код выхода.|  
|`FormatMessageFromSystem`|Необязательный параметр. Определяет, следует ли использовать системные ошибки сообщение, соответствующее коду выхода, или значение, указанное в `String`. Допустимые значения: `true`, что означает использование системные ошибки, и `false`, означающее использовать строку, предоставляемые `String`. Значение по умолчанию — `false`. Если это свойство имеет `false`, но `String` не задано, будет использоваться системные ошибки.|  
  
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
 [Элемент \<InstallChecks>](../deployment/installchecks-element-bootstrapper.md)
