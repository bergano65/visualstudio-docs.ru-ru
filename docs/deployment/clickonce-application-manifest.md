---
title: "Манифест приложения ClickOnce | Microsoft Docs"
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
  - "манифесты приложений [ClickOnce]"
  - "ClickOnce, манифесты приложений"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Манифест приложения ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] XML\-файл с описанием приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Манифесты приложения[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] имеют следующие элементы и атрибуты.  
  
|Элемент|Описание|Атрибуты|  
|-------------|--------------|--------------|  
|[Элемент \<assembly\>](../deployment/assembly-element-clickonce-application.md)|Обязательный.  Элемент верхнего уровня.|`manifestVersion`|  
|[Элемент \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)|Обязательный.  Определяет основную сборку приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[Элемент \<trustInfo\>](../deployment/trustinfo-element-clickonce-application.md)|Определяет требования безопасности приложения.|None|  
|[Элемент \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md)|Обязательный.  Определяет точку входа в код приложения.|`name`|  
|[Элемент \<dependency\>](../deployment/dependency-element-clickonce-application.md)|Обязательный.  Определяет все зависимости, необходимые для выполнения приложения.  При необходимости определяет сборки, которые требуется установить предварительно.|None|  
|[Элемент \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|Необязательный.  Определяет все не являющиеся сборками файлы, используемые приложением.  Может включать данные изоляции COM, связанные с этим файлом.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[Элемент \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md)|Необязательный.  Определяет расширение файла, которое требуется связать с приложением.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Заметки  
 Файл манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] определяет приложение развертыванное с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Дополнительные сведения о [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] см. в разделе [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## Расположение файлов  
 Манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] относящихся к одной версии развертывания.  По этой причине они должны храниться отдельно от манифестов развертывания.  Обычно такие файлы размещаются в папке, название которой соответствует версии.  
  
 Манифест приложения необходимо всегда подписывать до развертывания.  При изменении манифеста приложения вручную необходимо использовать программу mage.exe для повторной подписи манифеста приложения, обновления манифеста развертывания и повторной подписи этого манифеста развертывания.  Дополнительные сведения см. в разделе [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Синтаксис имени файла  
 Имя файла манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] должно быть полным именем и расширением приложения, как указано в элементе `assemblyIdentity`, с расширением manifest.  Например, манифест приложения Example.exe будет иметь следующее имя файла.  
  
 `example.exe.manifest`  
  
## Пример  
 В следующем примере кода показан манифест приложения для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
  
## См. также  
 [Публикация ClickOnce\-приложений](../deployment/publishing-clickonce-applications.md)