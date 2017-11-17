---
title: "Как: укажите URL-адрес поддержки для отдельных предварительных условий в развертывании ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2335c0279c8e7a23e1b514a8264651e73fedebfc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Практическое руководство. Указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce
Объект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания можно проверить число необходимых компонентов, которые должны быть доступны на клиентском компьютере для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для запуска приложения. К ним относятся требуемая Минимальная версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], версии операционной системы и все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], однако не может выполнить любые из этих предварительных условий самостоятельно. Если необходимый компонент не найден, он просто останавливает установку и отображает диалоговое окно, объясняющий, почему произошел сбой установки.  
  
 Существует два способа установки необходимых компонентов. Можно установить их, используя приложение загрузчика. Кроме того можно указать URL-адрес поддержки для отдельных предварительных условий, которая отображается для пользователей в диалоговом окне при готовности к установке не найден. Страницы, на который указывает этот URL-адрес может содержать ссылки на инструкции по установке необходимый компонент. Если приложение не указывает URL-адрес поддержки для отдельного предварительного условия [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает поддержки URL-адрес, указанный в манифесте развертывания для приложения в целом, если он определен.  
  
 Хотя [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe и MageUI.exe может быть использован для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертываний, ни один из этих средств непосредственно не поддерживает задание URL-адрес поддержки для отдельных предварительных условий. В этом документе описывается изменить для развертывания манифест приложения и манифест развертывания, чтобы включить эти вспомогательные URL-адреса.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Указание URL-адрес поддержки для отдельного предварительного условия  
  
1.  Откройте манифест приложения (файл с расширением MANIFEST) для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.  
  
2.  Необходимый компонент операционной системы, добавьте `supportUrl` атрибут `dependentOS` элемента:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Необходимым условием для определенной версии среды CLR, добавьте `supportUrl` атрибут `dependentAssembly` запись, которая задает зависимость среды выполнения:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Необходимым условием для сборки, должны быть предварительно установлены в глобальном кэше сборок, задайте `supportUrl` для `dependentAssembly` элемент, который задает требуемую сборку:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Необязательно. Для приложений, предназначенных для .NET Framework 4, откройте манифест развертывания (.application-файл) для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.  
  
6.  Необходимый компонент .NET Framework 4, добавьте `supportUrl` атрибут `compatibleFrameworks` элемента:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  После манифест приложения изменен вручную, необходимо заново подписать манифест приложения с помощью сертификата, а затем обновлять и заново подписать манифест развертывания. Необходимо использовать Mage.exe или MageUI.exe из набора SDK средств для выполнения этой задачи, как при создании этих файлов с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] стирает внесенные вручную. Дополнительные сведения об использовании Mage.exe повторной подписи манифестов см. в разделе [как: повторно подписать приложение и манифесты развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 URL-адрес поддержки не отображается в диалоговом окне, если оно помечено для выполнения в режиме частичного доверия.  
  
## <a name="see-also"></a>См. также  
 [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Пошаговое руководство. Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)