---
title: URL-адрес поддержки для необходимых компонентов в развертывании ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf115ad6ce8fb589e9b1c617f40053cf95af2b9c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263209"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Практическое руководство. указание URL-адреса поддержки для определенных необходимых компонентов в развертывании ClickOnce
Объект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания можно проверить ряд необходимых условий, которые должны быть доступны на клиентском компьютере для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для запуска приложения. Эти зависимости включают требуемая Минимальная версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], версию операционной системы и все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], тем не менее, не может выполнить любые из этих предварительных требований; Если необходимый компонент не найден, он просто останавливает установку и отображает диалоговое окно, объясняющее, почему произошел сбой установки.

 Существует два способа установки необходимых компонентов. Вы можете установить их, используя приложение начальной загрузки. Кроме того можно указать URL-адрес поддержки для определенных необходимых компонентов, который отображается для пользователей в диалоговом окне, если не найден необходимый компонент. Страница ссылается на этот URL-адрес может содержать ссылки на инструкции по установке этот необходимый компонент. Если приложение не указывает URL-адрес поддержки для отдельного предварительного условия, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает URL-адрес поддержки, указанной в манифесте развертывания для приложения в целом, если он определен.

 Хотя [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, и *MageUI.exe* все используется для создания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертываний, ни один из этих средств непосредственно не поддерживает задание URL-адрес поддержки для отдельных Предварительные требования. В этом документе описывается изменение развертывания манифест приложения и манифест развертывания, чтобы включить эти поддерживает URL-адреса.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Укажите URL-адрес поддержки для отдельного предварительного условия

1. Откройте манифест приложения ( *.manifest* файл) для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.

2. В список обязательных компонентов операционной системы, добавьте `supportUrl` атрибут `dependentOS` элемента:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Необходимым условием для определенной версии среды CLR, добавить `supportUrl` атрибут `dependentAssembly` запись, которая задает зависимость среды выполнения:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Необходимым условием для сборки, должны быть предварительно установлены в глобальном кэше сборок, задайте `supportUrl` для `dependentAssembly` элемент, задающий нужную сборку:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Необязательный параметр. Для приложений, предназначенных для .NET Framework 4, откройте манифест развертывания ( *.application* файл) для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в текстовом редакторе.

6. .NET Framework 4 перед началом добавления `supportUrl` атрибут `compatibleFrameworks` элемента:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Как только вы вручную изменить манифест приложения, необходимо повторно подписать манифест приложения с помощью сертификата, а затем обновить и повторно подписать манифест развертывания. Используйте *Mage.exe* или *MageUI.exe* средства пакета SDK для выполнения этой задачи, как при создании этих файлов с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] стирает внесенные вручную. Дополнительные сведения об использовании Mage.exe для повторной подписи манифестов см. в разделе [как: Повторно подписать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>безопасность платформы .NET Framework
 URL-адрес поддержки не отображается в диалоговом окне, если приложение помечено для запуска в режиме частичного доверия.

## <a name="see-also"></a>См. также
- [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)