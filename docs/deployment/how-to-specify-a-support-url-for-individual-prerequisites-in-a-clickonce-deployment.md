---
title: Поддержка URL-адресов для необходимых компонентов в развертывании ClickOnce
description: Узнайте, как развертывание ClickOnce проверяет наличие необходимых компонентов для запуска приложения ClickOnce и то, как развертывание работает с недостающими необходимыми компонентами.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 585ea1a558b91ac733670ad94a9a3e0be33f1348
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876320"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Практическое руководство. Указание URL-адреса службы поддержки для определенных компонентов, необходимых для развертывания ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Развертывание может проверить наличие ряда предварительных требований, которые должны быть доступны на клиентском компьютере для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запуска приложения. Эти зависимости включают требуемую минимальную версию платформа .NET Framework, версию операционной системы и все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], однако, не может установить ни один из этих компонентов. Если необходимый компонент не найден, он просто останавливает установку и отображает диалоговое окно, объясняющее причину сбоя установки.

 Существует два способа установки необходимых компонентов. Их можно установить с помощью приложения начального загрузчика. Кроме того, можно указать URL-адрес поддержки для отдельных необходимых компонентов, которые отображаются для пользователей в диалоговом окне, если необходимый компонент не найден. Страница, на которую ссылается этот URL-адрес, может содержать ссылки на инструкции по установке необходимого компонента. Если приложение не указывает URL-адрес поддержки для отдельного необходимого компонента, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает URL-адрес поддержки, указанный в манифесте развертывания для приложения в целом, если он определен.

 Хотя [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , *Mage.exe* и *MageUI.exe* можно использовать для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертываний, ни одно из этих средств не поддерживает непосредственное указание URL-адреса поддержки для отдельных необходимых компонентов. В этом документе описывается, как изменить манифест приложения и манифест развертывания развертывания, чтобы включить эти URL-адреса поддержки.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Укажите URL-адрес поддержки для отдельного необходимого компонента

1. Откройте манифест приложения (файл *manifest* ) для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.

2. Для необходимых компонентов операционной системы добавьте `supportUrl` атрибут к `dependentOS` элементу:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Для предварительного требования к определенной версии среды CLR добавьте `supportUrl` атрибут в `dependentAssembly` запись, указывающую зависимость среды CLR:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Для предварительного требования к сборке, которая должна быть предустановлена в глобальном кэше сборок, задайте `supportUrl` для `dependentAssembly` элемента, указывающего требуемую сборку:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Необязательный элемент. Для приложений, предназначенных для платформа .NET Framework 4, откройте манифест развертывания (файл *. Application* ) для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.

6. Для платформа .NET Framework 4 необходимых компонентов добавьте `supportUrl` атрибут к `compatibleFrameworks` элементу:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. После изменения манифеста приложения вручную необходимо повторно подписать манифест приложения с помощью цифрового сертификата, а затем обновить и повторно подписать манифест развертывания. Для выполнения этой задачи используйте средства пакета SDK *Mage.exe* или *MageUI.exe* , так как повторное создание этих файлов с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] удаления изменений вручную. Дополнительные сведения об использовании Mage.exe для повторного подписания манифестов см. [в разделе как повторно подписывать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>безопасность платформы .NET Framework
 URL-адрес поддержки не отображается в диалоговом окне, если приложение помечено для выполнения в режиме частичного доверия.

## <a name="see-also"></a>См. также раздел
- [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Элемент \<compatibleFrameworks>](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)