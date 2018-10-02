---
title: 'Практическое: укажите URL-адрес поддержки для определенных необходимых компонентов в развертывании ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 99003812248a10ca8797a5727911caf4ba3a0a60
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557629"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Практическое руководство. Указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите URL-адрес поддержки для определенных необходимых компонентов в развертывании ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment).  
  
Объект [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания можно проверить ряд необходимых условий, которые должны быть доступны на клиентском компьютере для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] для запуска приложения. К ним относятся требуемая Минимальная версия [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], версию операционной системы и все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], тем не менее, не может выполнить любые из этих предварительных требований; Если необходимый компонент не найден, он просто останавливает установку и отображает диалоговое окно, объясняющее, почему произошел сбой установки.  
  
 Существует два способа установки необходимых компонентов. Вы можете установить их, используя приложение начальной загрузки. Кроме того можно указать URL-адрес поддержки для определенных необходимых компонентов, который отображается для пользователей в диалоговом окне, если не найден необходимый компонент. Страница ссылается на этот URL-адрес может содержать ссылки на инструкции по установке этот необходимый компонент. Если приложение не указывает URL-адрес поддержки для отдельного предварительного условия, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] отображает URL-адрес поддержки, указанной в манифесте развертывания для приложения в целом, если он определен.  
  
 Хотя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe и MageUI.exe можно будет использовать для создания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертываний, ни один из этих средств непосредственно не поддерживает задание URL-адрес поддержки для определенных необходимых компонентов. В этом документе описывается изменение развертывания манифест приложения и манифест развертывания, чтобы включить эти поддерживает URL-адреса.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Указание URL-адрес поддержки для отдельного предварительного условия  
  
1.  Откройте манифест приложения (файл с расширением MANIFEST) для вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения в текстовом редакторе.  
  
2.  В список обязательных компонентов операционной системы, добавьте `supportUrl` атрибут `dependentOS` элемента:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Необходимым условием для определенной версии среды CLR, добавить `supportUrl` атрибут `dependentAssembly` запись, которая задает зависимость среды выполнения:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Необходимым условием для сборки, должны быть предварительно установлены в глобальном кэше сборок, задайте `supportUrl` для `dependentAssembly` элемент, задающий нужную сборку:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Необязательный. Для приложений, предназначенных для .NET Framework 4, откройте манифест развертывания (.application файл) для вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения в текстовом редакторе.  
  
6.  .NET Framework 4 перед началом добавления `supportUrl` атрибут `compatibleFrameworks` элемента:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Как только вы вручную изменить манифест приложения, необходимо повторно подписать манифест приложения с помощью сертификата, а затем обновить и повторно подписать манифест развертывания. Необходимо использовать Mage.exe или MageUI.exe из набора SDK средств для выполнения этой задачи, как при создании этих файлов с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] стирает внесенные вручную. Дополнительные сведения об использовании Mage.exe для повторной подписи манифестов см. в разделе [как: RE-Sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 URL-адрес поддержки не отображается в диалоговом окне, если приложение помечено для запуска в режиме частичного доверия.  
  
## <a name="see-also"></a>См. также  
 [Mage.exe (средство создания и редактирования манифеста)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Пошаговое руководство. Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)



