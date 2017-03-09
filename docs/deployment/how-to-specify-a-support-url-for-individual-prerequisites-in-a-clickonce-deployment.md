---
title: "Практическое руководство. Указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce | Microsoft Docs"
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
  - "развертывание ClickOnce, необходимые компоненты"
  - "развертывание ClickOnce, URL-адреса"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] может проверять ряд предварительных условий, которые должны соблюдаться на клиентском компьютере для выполнения приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Эти условия включают требуемую минимальную версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], версию операционной системы и версии всех сборок, которые должны быть предварительно установлены в глобальном кэше сборок.  Однако [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не может выполнить любые из этих предварительных условий самостоятельно. Если предварительное условие не соблюдено, установка просто останавливается, и появляется диалоговое окно, содержащее объяснение, почему установка не завершилась успешно.  
  
 Существует два метода установки компонентов, составляющих предварительные условия.  Их можно установить с помощью приложения загрузчика.  В альтернативном варианте можно задать для отдельных предварительных условий вспомогательный URL\-адрес, который отображается для пользователей в диалоговом окне, если предварительное условие не найдено.  Страница, на которую ссылаются с помощью этого URL\-адреса, может содержать ссылки на инструкции по установке требуемого предварительного условия.  Если приложением не задается вспомогательный URL\-адрес для отдельного предварительного условия, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает вспомогательный URL\-адрес, указываемый в манифесте развертывания для приложения в целом, если манифест определен.  
  
 Хотя [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe и MageUI.exe могут все использоваться для создания развертываний [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ни одно из этих средств непосредственно не поддерживает задание вспомогательного URL\-адреса для отдельных необходимых компонентов.  В этом документе описывается, как изменить для развертывания манифест приложения и манифест развертывания, чтобы включить эти вспомогательные URL\-адреса.  
  
### Задание вспомогательного URL\-адреса для отдельного предварительного условия  
  
1.  Откройте манифест приложения \(файл с расширением MANIFEST\) для своего приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] в текстовом редакторе.  
  
2.  Для предварительного условия операционной системы добавьте атрибут `supportUrl` в элемент `dependentOS`:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  С целью соблюдения предварительного требования по определенной версии общеязыковой среды выполнения добавьте атрибут `supportUrl` в запись `dependentAssembly`, которая задает зависимость общеязыковой среды выполнения:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  С целью соблюдения предварительного условия по сборке, которая должна быть предустановлена в глобальном кэше сборок, установите `supportUrl` для элемента `dependentAssembly`, указывающего требуемую сборку:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Необязательный.  Для приложений, предназначенных для .NET Framework 4, откройте манифест развертывания \(файл с расширением APPLICATION\) для своего приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] в текстовом редакторе.  
  
6.  Чтобы добавить .NET Framework 4 в качестве необходимого компонента, добавьте в элемент `compatibleFrameworks` атрибут `supportUrl`:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  После того как манифест приложения изменен вручную, необходимо заново подписать манифест приложения с использованием своего цифрового сертификата, а затем также обновить и переподписать манифест развертывания.  Для выполнения этой задачи необходимо использовать средства Mage.exe или MageUI.exe из набора SDK, так как при создании этих файлов с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] удаляются изменения, внесенные вручную.  Дополнительные сведения об использовании Mage.exe для переподписания манифестов см. в разделе [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Безопасность платформы .NET Framework  
 Вспомогательный URL\-адрес не отображается в диалоговом окне, если приложение помечено для выполнения с определенным уровнем доверия.  
  
## См. также  
 [Mage.exe \(средство создания и редактирования манифеста\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Элемент \<compatibleFrameworks\>](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Предварительные условия для развертывания приложения](../deployment/application-deployment-prerequisites.md)