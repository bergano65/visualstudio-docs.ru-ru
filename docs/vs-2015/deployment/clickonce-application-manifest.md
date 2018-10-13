---
title: Манифест приложения ClickOnce | Документация Майкрософт
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
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 57e48816ede7210a268cc465da1eee3b6ff43d02
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289592"
---
# <a name="clickonce-application-manifest"></a>ClickOnce Application Manifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения является XML-файл, описывающий приложение, которое развертывается с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесты приложений имеют следующие элементы и атрибуты.  
  
|Элемент|Описание|Атрибуты|  
|-------------|-----------------|----------------|  
|[\<сборка > элемент](../deployment/assembly-element-clickonce-application.md)|Обязательно. Это элемент верхнего уровня.|`manifestVersion`|  
|[\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md)|Обязательно. Определяет основную сборку из [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo > элемент](../deployment/trustinfo-element-clickonce-application.md)|Определяет требования к безопасности приложения.|Нет|  
|[\<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md)|Обязательно. Определяет точку входа в код приложения.|`name`|  
|[\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)|Обязательно. Определяет все зависимости, необходимые для выполнения приложения. При необходимости определяет сборки, которые требуется установить предварительно.|Нет|  
|[Элемент \<file>](../deployment/file-element-clickonce-application.md)|Необязательный. Идентифицирует каждого файла не являющиеся сборками, который используется приложением. Может включать данные изоляции модели COM, связанные с этим файлом.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md)|Необязательный. Определяет расширение файла, нужно связать с приложением.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Файл манифеста приложения определяет приложение, развернутое с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Дополнительные сведения о [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] см. в разделе [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Расположение файлов  
 Объект [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения относится к отдельной версии развертывания. По этой причине они должны храниться отдельно от манифеста развертывания. Распространенный способ — разместить их в подкаталоге соответствующая версия.  
  
 Манифест приложения всегда должны быть подписаны перед развертыванием. Если вы вручную измените манифест приложения, необходимо использовать mage.exe повторно подписать манифест приложения, обновить манифест развертывания и затем повторно подписать манифест развертывания. Дополнительные сведения см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Синтаксис имени файла  
 Имя [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] файла манифеста приложения должно быть полное имя и расширение приложения, как указано в `assemblyIdentity` элемент, а затем расширение manifest. Например манифест приложения, который ссылается на приложение Example.exe используется следующий синтаксис имени файла.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан манифест приложения для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
```  
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
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)



