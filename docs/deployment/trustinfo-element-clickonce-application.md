---
title: '&lt;&gt;элемент trustInfo (приложение ClickOnce) | Документация Майкрософт'
description: Элемент trustInfo описывает минимальные разрешения безопасности, необходимые для запуска приложения на клиентском компьютере. Элемент trustInfo является обязательным.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e91bdb2e842692224564374e3f9f4d23cf71cf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945023"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>Элемент &lt;trustInfo&gt; (приложение ClickOnce)
Описывает минимальные разрешения безопасности, необходимые для запуска приложения на клиентском компьютере.

## <a name="syntax"></a>Синтаксис

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `trustInfo` является обязательным и находится в пространстве имен `asm.v2` . Он не содержит атрибуты, но содержит следующие элементы.

## <a name="security"></a>security
 Обязательный элемент. Этот элемент является дочерним по отношению к элементу `trustInfo` . Он содержит элемент `applicationRequestMinimum` и не содержит атрибуты.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Обязательный элемент. Этот элемент является дочерним по отношению к элементу `security` и содержит элементы `PermissionSet`, `assemblyRequest`и `defaultAssemblyRequest`. Этот элемент не содержит атрибуты.

## <a name="permissionset"></a>PermissionSet
 Обязательный элемент. Этот элемент является дочерним по отношению к элементу `applicationRequestMinimum` и содержит элемент `IPermission` . Этот элемент содержит следующие атрибуты.

- `ID`

     Обязательный элемент. Обозначает набор разрешений. Этот атрибут может быть любым значением. На идентификатор указывается ссылка в атрибутах `defaultAssemblyRequest` и `assemblyRequest` .

- `version`

     Обязательный элемент. Обозначает версию разрешения. Обычное значение — `1`.

## <a name="ipermission"></a>IPermission
 Необязательный элемент. Этот элемент является дочерним по отношению к элементу `PermissionSet` . `IPermission`Элемент полностью определяет класс разрешения в платформа .NET Framework. Элемент `IPermission` содержит следующие атрибуты, но может иметь и атрибуты дополнительные, соответствующие свойствам в классе разрешений. Чтобы узнать синтаксис конкретного разрешения, см. примеры, перечисленные в файле Security.config.

- `class`

     Обязательный элемент. Обозначает класс разрешений по строгому имени. Например, следующий код обозначает тип `FileDialogPermission` .

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Обязательный элемент. Обозначает версию разрешения. Обычное значение — `1`.

- `Unrestricted`

     Обязательный элемент. Определяет, требуется ли приложению неограниченная версия конкретного разрешения. Если значение равно `true`, неограниченная версия разрешения строго обязательна. Если значение равно `false`или этот атрибут не определен, на него распространяются ограничения в соответствии с атрибутами конкретного разрешения, заданными в теге `IPermission` . Примите следующие разрешения:

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     В этом примере объявление для <xref:System.Security.Permissions.EnvironmentPermission> разрешает приложению только чтение переменной среды USERNAME, тогда как объявление для <xref:System.Security.Permissions.FileDialogPermission> предоставляет приложению неограниченное право на использование всех классов <xref:System.Windows.Forms.FileDialog> .

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 Необязательный элемент. Обозначает набор разрешений, предоставленных всем сборкам. Этот элемент является дочерним по отношению к элементу `applicationRequestMinimum` и содержит следующий атрибут.

- `permissionSetReference`

     Обязательный элемент. Определяет идентификатор набора разрешений, который является разрешением по умолчанию. Набор разрешений объявляется в элементе `PermissionSet` .

## <a name="assemblyrequest"></a>assemblyRequest
 Необязательный элемент. Обозначает разрешения для конкретной сборки. Этот элемент является дочерним по отношению к элементу `applicationRequestMinimum` и содержит следующие атрибуты.

- `Name`

     Обязательный элемент. Обозначает имя сборки.

- `permissionSetReference`

     Обязательный элемент. Определяет идентификатор набора разрешений, требующийся для этой сборки. Набор разрешений объявляется в элементе `PermissionSet` .

## <a name="requestedprivileges"></a>requestedPrivileges
 Необязательный элемент. Этот элемент является дочерним по отношению к элементу `security` и содержит элемент `requestedExecutionLevel` . Этот элемент не содержит атрибуты.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 Необязательный элемент. Определяет уровень безопасности, в рамках которого приложение запрашивает выполнение. Этот элемент не содержит дочерние элементы и содержит следующие атрибуты.

- `Level`

   Обязательный элемент. Указывает уровень безопасности, запрошенный приложением. Доступны следующие значения:

   `asInvoker`: дополнительные разрешения не запрашиваются. Для этого уровня не требуются дополнительные запросы о доверии.

   `highestAvailable`: запрашиваются разрешения наивысшего уровня, доступные родительскому процессу.

   `requireAdministrator`: запрашиваются полные права администратора.

   Приложения[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] могут устанавливаться только при указании значения `asInvoker`. Установка с другим значением завершится сбоем.

- `uiAccess`

   Необязательный элемент. Указывает, требуется ли приложению доступ к защищенным элементам пользовательского интерфейса. Доступные значения: `true` или `false`; значение по умолчанию — false. Только для подписанных приложений требуется значение true.

## <a name="remarks"></a>Remarks
 Если приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запрашивает больше разрешений, чем клиентский компьютер предоставит по умолчанию, диспетчер доверия среды CLR спросит пользователя, следует ли предоставить приложению повышенный уровень доверия. Если ответ — "нет", приложение не будет запущено; в противном случае оно будет запущено с запрошенными разрешениями.

 Все разрешения, запрошенные через `defaultAssemblyRequest` и `assemblyRequest` , будут предоставлены без вывода запросов пользователям, если манифест развертывания содержит действительную лицензию доверия.

 Дополнительные сведения о повышении уровня разрешений см. в разделе [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md). Дополнительные сведения о развертывании политик см. в статье [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Примеры
 В следующих трех примерах кода показаны элементы `trustInfo` для зон безопасности, именованных по умолчанию — Internet, LocalIntranet и FullTrust. Их можно использовать в манифесте приложения развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 В первом примере показан элемент `trustInfo` для разрешений по умолчанию, доступных в зоне безопасности Internet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Во втором примере показан элемент `trustInfo` для разрешений по умолчанию, доступных в зоне безопасности LocalIntranet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 В третьем примере показан элемент `trustInfo` для разрешений по умолчанию, доступных в зоне безопасности FullTrust.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>См. также раздел
- [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)