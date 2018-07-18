---
title: Манифест развертывания ClickOnce | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd67f3db61662535a0a8522575e716886602f5b7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560327"
---
# <a name="clickonce-deployment-manifest"></a>Манифест развертывания ClickOnce
Манифест развертывания — это XML-файл, который описывает развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], включая идентификацию текущей версии приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для развертывания.  
  
 Манифесты развертывания имеют следующие элементы и атрибуты.  
  
|Элемент|Описание|Атрибуты|  
|-------------|-----------------|----------------|  
|[\<сборка > элемент](../deployment/assembly-element-clickonce-deployment.md)|Обязательно. Это элемент верхнего уровня.|`manifestVersion`|  
|[\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-deployment.md)|Обязательно. Идентифицирует манифест приложения для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<Описание > элемент](../deployment/description-element-clickonce-deployment.md)|Обязательно. Определение сведений о приложении, используемый для создания оболочки присутствия и **Установка и удаление программ** элемента панели управления.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<Развертывание > элемент](../deployment/deployment-element-clickonce-deployment.md)|Необязательный. Идентифицирует атрибуты, используемые для развертывания обновлений и доступа к системе.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Обязательно. Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.|`SupportUrl`|  
|[\<зависимость > элемент](../deployment/dependency-element-clickonce-deployment.md)|Обязательно. Идентифицирует устанавливаемую версию приложения для развертывания и местоположение манифеста приложения.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity > элемент](../deployment/publisheridentity-element-clickonce-deployment.md)|Является обязательным для манифестов с подписью. Содержит сведения об издателе, подписавшем этот манифест развертывания.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Подпись > элемент](../deployment/signature-element-clickonce-deployment.md)|Необязательный. Содержит сведения, необходимые для того, чтобы подписать этот манифест развертывания с помощью цифровой подписи.|Нет|  
|[\<customErrorReporting > элемент](../deployment/customerrorreporting-element-clickonce-deployment.md)|Необязательный. Задает отображаемый в случае ошибки URI.|URI|  
  
## <a name="remarks"></a>Примечания  
 Файл манифеста развертывания определяет развертывание приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], включая текущую версию и другие настройки развертывания. Он ссылается на манифест приложения, описывающий текущую версию приложения и все файлы, задействованные в развертывании.  
  
 Для получения дополнительной информации см. [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Расположение файлов  
 Файл манифеста развертывания ссылается на правильный манифест приложения для текущей версии приложения. Когда новая версия развертывания приложения становится доступной, необходимо обновить манифест развертывания, чтобы он ссылался на новый манифест приложения.  
  
 Файл манифеста развертывания должен иметь строгое имя и может также содержать сертификаты для проверки издателя.  
  
## <a name="file-name-syntax"></a>Синтаксис имени файла  
 Имя файла манифеста развертывания должно оканчиваться расширением .application.  
  
## <a name="examples"></a>Примеры  
 Манифест развертывания показан в следующем примере кода.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)