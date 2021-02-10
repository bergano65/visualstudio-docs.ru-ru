---
title: Манифест приложения ClickOnce | Документация Майкрософт
description: Сведения о манифесте приложения ClickOnce, который представляет собой XML-файл, описывающий приложение, которое развертывается с помощью ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccd8389859de3ffce7b04e2da648b2ac2e807a79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936188"
---
# <a name="clickonce-application-manifest"></a>Манифест приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Манифест приложения — это XML-файл, описывающий приложение, которое развертывается с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Манифесты приложений имеют следующие элементы и атрибуты.

| Элемент | Описание | Атрибуты |
| - | - | - |
| [\<assembly> Элемент](../deployment/assembly-element-clickonce-application.md) | Обязательный элемент. Это элемент верхнего уровня. | `manifestVersion` |
| [\<assemblyIdentity> Элемент](../deployment/assemblyidentity-element-clickonce-application.md) | Обязательный элемент. Определяет основную сборку [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Элемент](../deployment/trustinfo-element-clickonce-application.md) | Определяет требования к безопасности приложения. | Отсутствуют |
| [\<entryPoint> Элемент](../deployment/entrypoint-element-clickonce-application.md) | Обязательный элемент. Определяет точку входа кода приложения. | `name` |
| [\<dependency> Элемент](../deployment/dependency-element-clickonce-application.md) | Обязательный элемент. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно. | Отсутствуют |
| [\<file> Элемент](../deployment/file-element-clickonce-application.md) | Необязательный элемент. Определяет каждый несборочный файл, используемый приложением. Может включать данные изоляции модели COM, связанные с этим файлом. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Элемент](../deployment/fileassociation-element-clickonce-application.md) | Необязательный элемент. Определяет расширение файла, связываемое с приложением. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Remarks
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Файл манифеста приложения определяет приложение, развернутое с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Дополнительные сведения о [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] см. в разделе [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Размещение файла
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Манифест приложения относится только к одной версии развертывания. По этой причине они должны храниться отдельно от манифестов развертывания. Распространенное соглашение заключается в том, что они помещаются в подкаталог, названный после соответствующей версии.

 Манифест приложения всегда должен быть подписан до развертывания. При изменении манифеста приложения вручную необходимо использовать *mage.exe* для повторной подписи манифеста приложения, обновления манифеста развертывания, а затем повторной подписи манифеста развертывания. Дополнительные сведения см. [в разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Синтаксис имени файла
 Имя файла манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] должно содержать полное имя и расширение приложения, определенные в элементе `assemblyIdentity`, и иметь расширение *MANIFEST*. Например, манифест приложения, который ссылается на *Example.exe* приложение, будет использовать следующий синтаксис имени файла.

 `example.exe.manifest`

## <a name="example"></a>Пример
 В следующем примере кода показан манифест приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>См. также раздел
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)