---
title: 'Практическое: Добавление надежного издателя на клиентский компьютер для приложений ClickOnce | Документация Майкрософт'
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
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fb888e95bb27ce41945f8d50e6a0ed0e763df133
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570566"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Инструкции: добавление надежного издателя на клиентский компьютер для приложений ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Add a Trusted Publisher на клиентский компьютер для приложений ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
С помощью технологии развертывания доверенных приложений можно настроить клиентские компьютеры так, чтобы ваши приложения [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] выполнялись с более высоким уровнем доверия без вывода запроса пользователю. Следующие процедуры показывают, как использовать программу командной строки CertMgr.exe для добавления сертификата издателя в хранилище надежных издателей на клиентском компьютере.  
  
 Используемые команды могут незначительно отличаться в зависимости от того, является ли центр сертификации (ЦС), выдавший сертификат, частью доверенной корневой области клиента. Если клиентский компьютер Windows входит в состав домена, он будет содержать перечень доверенных корневых центров сертификации. Обычно этот список настраивается системным администратором. Если сертификат был выдан одним из этих доверенных корневых ЦС либо центром, связанным с одним из таких доверенных корневых ЦС, его можно добавить в доверенное корневое хранилище клиента. С другой стороны, если сертификат не был выдан одним из этих доверенных корневых ЦС, необходимо добавить его как в доверенное корневое хранилище клиента, так и в хранилище надежных издателей.  
  
> [!NOTE]
>  Подобным образом следует добавить сертификаты на каждый клиентский компьютер, где вы планируете развернуть приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], которое требует повышенного уровня разрешений. Сертификаты добавляются вручную или с помощью приложения, развернутого на клиентских компьютерах. Эти компьютеры нужно настроить всего один раз, после чего можно развернуть любое число приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], подписанных с помощью того же сертификата.  
  
 Кроме того, можно добавить сертификат в хранилище программным способом с помощью класса <xref:System.Security.Cryptography.X509Certificates.X509Store> .  
  
 Общие сведения о развертывании доверенных приложений см. в разделе [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Добавление сертификата в хранилище надежных издателей в доверенной корневой области  
  
1.  Получите цифровой сертификат в центре сертификации.  
  
2.  Экспортируйте сертификат в формат Base64 X.509 (CER). Дополнительные сведения о форматах сертификатов см. в разделе [Экспорт сертификата](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  В командной строке на клиентских компьютерах выполните следующую команду:  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Добавление сертификата в хранилище надежных издателей в другой корневой области  
  
1.  Получите цифровой сертификат в центре сертификации.  
  
2.  Экспортируйте сертификат в формат Base64 X.509 (CER). Дополнительные сведения о форматах сертификатов см. в разделе [Экспорт сертификата](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  В командной строке на клиентских компьютерах выполните следующую команду:  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Практическое руководство. Включение параметров безопасности ClickOnce-приложений.](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Практическое руководство. Установка зоны безопасности для ClickOnce-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Практическое руководство. Отладка ClickOnce-приложения с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Практическое: Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Практическое: повторной подписи манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Практическое руководство. Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)



