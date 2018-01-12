---
title: "Присвоение уровня доверия решениям Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 41ecf50a7306025913f228500036d133918dd31b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="granting-trust-to-office-solutions"></a>Присвоение уровня доверия решениям Office
  Присвоение уровня доверия решениям Office означает изменение политики безопасности для каждого целевого компьютера, чтобы доверять сборку решения, манифест приложения, манифест развертывания и документа. Доверие может быть предоставлен для решения Office путем вы или конечным пользователем.  
  
 Можно предоставить полное доверие для решения Office, подписание манифестов приложения и развертывания.  
  
 Конечным пользователям можно предоставить доверие решения Office, делая решение о доверии в [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запрос о доверии.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>Предоставление доверия решению с помощью подписи приложения и развертывания манифестов  
 Все развертывания приложения и манифестов Office решения должны быть подписаны сертификатом, который идентифицирует издателя. Сертификаты обеспечивают основу для принятия решений о доверии.  
  
 Временный сертификат создается автоматически и предоставлено доверие во время сборки, поэтому решение будет выполняться во время отладки. Если вы публикуете решение, которое подписывается временный сертификат, пользователю будет предложено принять решение о доверии.  
  
 Если вход в решение с известным и надежным сертификатом решение автоматически будет выполнена без запроса пользователю принять решение о доверии. Дополнительные сведения о получении сертификата для подписи см. в разделе [ClickOnce и технология Authenticode](/visualstudio/deployment/clickonce-and-authenticode). После получения сертификата, сертификат должен быть явно доверенным, добавьте его в список доверенных издателей. Дополнительные сведения см. в разделе [как: Добавление надежных издателей на клиентский компьютер для приложений ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Если разработчик подписывает решение временным сертификатом, администратор может переподписать настройку с известным и надежным сертификатом с помощью манифеста средства создания и редактирования (mage.exe), которое является одним из средств Microsoft .NET Framework. Дополнительные сведения о подписи решений см. в разделе [как: решений Office входа](../vsto/how-to-sign-office-solutions.md) и [как: входа приложения и манифестов развертывания](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Предоставление доверия решению с помощью запрос о доверии ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]предлагает пользователю принять решение о доверии, если нет политики организации, которому доверяет сертификату решения. Если конечный пользователь предоставляет решению доверия, создается запись списка включения, содержащий URL-адрес и открытый ключ для хранения решения о доверии. Когда Настройка доверия выполняется более поздней версии, конечный пользователь не запрашиваются повторно.  
  
 Администраторы могут отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запросы о доверии или требуют, чтобы запросы возникали только для решений, которые подписаны с помощью сертификата Authenticode. Дополнительные сведения о том, как изменить эти параметры для зон MyComputer, локальная интрасеть, Интернет, TrustedSites и UntrustedSites см. в разделе [как: Настройка ClickOnce доверия поведения запроса](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md)   
 [Устранение неполадок безопасности решений Office](../vsto/troubleshooting-office-solution-security.md)   
 [Рекомендации по обеспечению безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  