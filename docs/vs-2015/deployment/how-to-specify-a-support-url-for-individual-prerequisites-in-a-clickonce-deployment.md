---
title: Как указать URL-адрес поддержки для отдельных необходимых компонентов в развертывании ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679969"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Практическое руководство. Указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Развертывание может проверить наличие ряда предварительных требований, которые должны быть доступны на клиентском компьютере для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] запуска приложения. К ним относятся необходимая минимальная версия [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , версия операционной системы и все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], однако, не может установить ни один из этих компонентов. Если необходимый компонент не найден, он просто останавливает установку и отображает диалоговое окно, объясняющее причину сбоя установки.  
  
 Существует два способа установки необходимых компонентов. Их можно установить с помощью приложения начального загрузчика. Кроме того, можно указать URL-адрес поддержки для отдельных необходимых компонентов, которые отображаются для пользователей в диалоговом окне, если необходимый компонент не найден. Страница, на которую ссылается этот URL-адрес, может содержать ссылки на инструкции по установке необходимого компонента. Если приложение не указывает URL-адрес поддержки для отдельного необходимого компонента, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] отображает URL-адрес поддержки, указанный в манифесте развертывания для приложения в целом, если он определен.  
  
 Хотя [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Mage.exe и MageUI.exe можно использовать для создания [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертываний, ни одно из этих средств не поддерживает непосредственное указание URL-адреса поддержки для отдельных необходимых компонентов. В этом документе описывается, как изменить манифест приложения и манифест развертывания развертывания, чтобы включить эти URL-адреса поддержки.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Указание URL-адреса поддержки для отдельного необходимого компонента  
  
1. Откройте манифест приложения (файл manifest) для своего [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения в текстовом редакторе.  
  
2. Для необходимых компонентов операционной системы добавьте `supportUrl` атрибут к `dependentOS` элементу:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Для предварительного требования к определенной версии среды CLR добавьте `supportUrl` атрибут в `dependentAssembly` запись, указывающую зависимость среды CLR:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Для предварительного требования к сборке, которая должна быть предустановлена в глобальном кэше сборок, задайте `supportUrl` для `dependentAssembly` элемента, указывающего требуемую сборку:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Необязательный элемент. Для приложений, предназначенных для .NET Framework 4, откройте манифест развертывания (файл. Application) для своего [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения в текстовом редакторе.  
  
6. Для .NET Framework 4 необходимых компонентов добавьте `supportUrl` атрибут к `compatibleFrameworks` элементу:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. После изменения манифеста приложения вручную необходимо повторно подписать манифест приложения с помощью цифрового сертификата, а затем обновить и повторно подписать манифест развертывания. Для выполнения этой задачи необходимо использовать средства пакета SDK Mage.exe или MageUI.exe, так как повторное создание этих файлов с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] удаления изменений вручную. Дополнительные сведения об использовании Mage.exe для повторного подписания манифестов см. [в разделе как повторно подписывать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 URL-адрес поддержки не отображается в диалоговом окне, если приложение помечено для выполнения в режиме частичного доверия.  
  
## <a name="see-also"></a>См. также:  
 [Mage.exe (Инструмент создания и изменения манифестов)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Дерев](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce и Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Необходимые условия для развертывания приложения](../deployment/application-deployment-prerequisites.md)
