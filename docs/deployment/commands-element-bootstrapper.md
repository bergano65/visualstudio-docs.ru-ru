---
title: '&lt;Элемент Commands &gt; (начальный загрузчик) | Документация Майкрософт'
description: Элемент Commands реализует тесты в элементах под Инсталлчеккс и объявляет пакет для установки в случае сбоя теста загрузчика ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f53ca683e40be8e3cc428d013d2b8d3c8c5773e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881234"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Элемент Commands &gt; (начальный загрузчик)
`Commands`Элемент реализует тесты, описанные элементами, расположенными под `InstallChecks` элементом, и объявляет, какой пакет [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] должен быть установлен загрузчиком в случае сбоя теста.

## <a name="syntax"></a>Синтаксис

```xml
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
 `Commands`Элемент является обязательным. Элемент имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`Reboot`|Необязательный элемент. Определяет, должна ли система перезапускаться, если любой из пакетов возвращает код выхода перезапуска. В следующем списке приведены допустимые значения:<br /><br /> `Defer`. Перезагрузка откладывается до некоторого времени в будущем.<br /><br /> `Immediate`. Приводит к немедленному перезапуску, если один из пакетов вернул код выхода перезапуска.<br /><br /> `None`. Вызывает игнорирование всех запросов на перезапуск.<br /><br /> Значение по умолчанию — `Immediate`.|

## <a name="command"></a>Get-Help
 Элемент `Command` является дочерним для элемента `Commands`. `Commands`Элемент может иметь один или несколько `Command` элементов. Элемент имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`PackageFile`|Обязательный элемент. Имя устанавливаемого пакета должно иметь одно или несколько условий, указанных параметром `InstallConditions` return false. Пакет должен быть определен в том же файле с помощью `PackageFile` элемента.|
|`Arguments`|Необязательный элемент. Набор аргументов командной строки для передачи в файл пакета.|
|`EstimatedInstallSeconds`|Необязательный элемент. Предполагаемое время в секундах, необходимое для установки пакета. Это значение определяет размер индикатора выполнения, который загрузчик отображает пользователю. Значение по умолчанию — 0. в этом случае временная оценка не указывается.|
|`EstimatedDiskBytes`|Необязательный элемент. Предполагаемый объем места на диске (в байтах), который будет занимать пакет после завершения установки. Это значение используется в требованиях к месту на жестком диске, которое загрузчик отображает пользователю. Значение по умолчанию — 0. в этом случае загрузчик не отображает требования к дисковому пространству.|
|`EstimatedTempBytes`|Необязательный элемент. Предполагаемый объем временного места на диске в байтах, которое потребуется пакету.|
|`Log`|Необязательный элемент. Путь к файлу журнала, создаваемому пакетом, относительно корневого каталога пакета.|

## <a name="installconditions"></a>инсталлкондитионс
 `InstallConditions`Элемент является дочерним по отношению к `Command` элементу. Каждый `Command` элемент может иметь не более одного `InstallConditions` элемента. Если `InstallConditions` элемент не существует, пакет, заданный параметром, `Condition` всегда будет выполняться.

## <a name="bypassif"></a>бипассиф
 `BypassIf`Элемент является дочерним для `InstallConditions` элемента и описывает положительное условие, при котором команда не должна выполняться. Каждый `InstallConditions` элемент может иметь ноль или более `BypassIf` элементов.

 `BypassIf` имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`Property`|Обязательный элемент. Имя тестируемого свойства. Свойство должно быть ранее определено дочерним `InstallChecks` элементом элемента. Дополнительные сведения см. в разделе [\<InstallChecks>Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Обязательный элемент. Тип выполняемого сравнения. В следующем списке приведены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Обязательный элемент. Значение для сравнения со свойством.|
|`Schedule`|Необязательный элемент. Имя `Schedule` тега, определяющего, когда должно оцениваться это правило.|

## <a name="failif"></a>фаилиф
 `FailIf`Элемент является дочерним для `InstallConditions` элемента и описывает положительное условие, при котором установка должна быть прервана. Каждый `InstallConditions` элемент может иметь ноль или более `FailIf` элементов.

 `FailIf` имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`Property`|Обязательный элемент. Имя тестируемого свойства. Свойство должно быть ранее определено дочерним `InstallChecks` элементом элемента. Дополнительные сведения см. в разделе [\<InstallChecks>Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Обязательный элемент. Тип выполняемого сравнения. В следующем списке приведены допустимые значения:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Обязательный элемент. Значение для сравнения со свойством.|
|`String`|Необязательный элемент. Текст, отображаемый пользователю при сбое.|
|`Schedule`|Необязательный элемент. Имя `Schedule` тега, определяющего, когда должно оцениваться это правило.|

## <a name="exitcodes"></a>ExitCodes
 `ExitCodes`Элемент является дочерним по отношению к `Command` элементу. `ExitCodes`Элемент содержит один или несколько `ExitCode` элементов, которые определяют, что должна делать установка в ответ на код выхода из пакета. Под элементом может быть один необязательный `ExitCode` элемент `Command` . `ExitCodes` не имеет атрибутов.

## <a name="exitcode"></a>ExitCode
 `ExitCode`Элемент является дочерним по отношению к `ExitCodes` элементу. `ExitCode`Элемент определяет, что должна делать установка в ответ на код выхода из пакета. `ExitCode` не содержит дочерних элементов и имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`Value`|Обязательный элемент. Значение кода выхода, к которому `ExitCode` применяется этот элемент.|
|`Result`|Обязательный элемент. Как установка должна реагировать на этот код выхода. В следующем списке приведены допустимые значения:<br /><br /> `Success`. Помечает пакет как успешно установленный.<br /><br /> `SuccessReboot`. Помечает пакет как успешно установленный и сообщает системе о необходимости перезапуска.<br /><br /> `Fail`. Помечает пакет как неудачный.<br /><br /> `FailReboot`. Помечает пакет как неудачный и сообщает системе о необходимости перезапуска.|
|`String`|Необязательный элемент. Значение, отображаемое пользователю в ответ на этот код выхода.|
|`FormatMessageFromSystem`|Необязательный элемент. Определяет, следует ли использовать предоставляемое системой сообщение об ошибке, соответствующее коду выхода, или использовать значение, указанное в `String` . Допустимые значения: `true` , что означает использование системной ошибки, и `false` , что означает использование строки, предоставленной `String` . Значение по умолчанию — `false`. Если это свойство имеет `false` значение, но `String` не задано, будет использоваться предоставляемая системой ошибка.|

## <a name="example"></a>Пример
 В следующем примере кода определяются команды для установки платформа .NET Framework 2,0.

```xml
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

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме продуктов и пакетов](../deployment/product-and-package-schema-reference.md)
- [Элемент \<InstallChecks>](../deployment/installchecks-element-bootstrapper.md)