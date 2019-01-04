---
title: Предоставление доверия решениям Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1acc6f73dd52bacdfd62aff3b2da62e559c4fda6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890473"
---
# <a name="grant-trust-to-office-solutions"></a>Предоставление доверия решениям Office
  Предоставление доверия Office решения означает изменение политики безопасности для каждого целевого компьютера на доверие сборке решения, манифест приложения, манифест развертывания и документа. Отношения доверия могут предоставляться для решения Office вы или конечным пользователем.

 Можно предоставить полное доверие для решения Office, подписание манифестов приложения и развертывания.

 Конечным пользователям можно предоставить доверие решения Office, сделав решение о доверии в [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запрос о доверии.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> Доверие, подписание манифестов приложения и развертывания решения
 Все приложения и развертывания манифесты для Office, решения должен быть подписан сертификатом, который идентифицирует издателя. Сертификаты обеспечивают основу для принятия решений о доверии.

 Временный сертификат создается для вас и предоставляются доверия во время сборки, поэтому решение будет выполняться во время его отладки. Если вы публикуете решение, которое подписывается временный сертификат, конечному пользователю будет предложено принять решение о доверии.

 Если вы подписываете решение с известным и надежным сертификатом, решение автоматически устанавливается без выдачи запроса пользователю принять решение о доверии. Дополнительные сведения о получении сертификата для подписи см. в разделе [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md). После получения сертификата, сертификат должен быть явно доверенным, добавьте его в список надежных издателей. Дополнительные сведения см. в разделе [Как Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Если разработчик выполняет решение с временный сертификат, администратор может переподписать настройку с известным и надежным сертификатом с помощью Manifest Generation and Editing Tool (*mage.exe*), которая является одной из Средства Microsoft .NET Framework. Дополнительные сведения о подписи решений, см. в разделе [как: Подписывание решений Office](../vsto/how-to-sign-office-solutions.md) и [как: Подписание манифестов приложения и развертывания](../ide/how-to-sign-application-and-deployment-manifests.md).

##  <a name="TrustPrompt"></a>Доверие решения с помощью запроса о доверии ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] предлагает пользователю принять решение о доверии, если нет политики во всей организации, которому доверяет сертификату решения. Если конечный пользователь предоставляет доверия решению, создается запись списка включения, содержащий URL-адрес и открытый ключ для хранения решения о доверии. Настройка доверия при выполнении более поздней версии, конечному пользователю не предлагается еще раз.

 Администраторы могут отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запросы о доверии или требовать, чтобы запросы возникали только для решений, которые подписаны с помощью сертификата Authenticode. Дополнительные сведения о том, как изменить эти настройки для зоны «Мой компьютер», локальная интрасеть, Интернет, TrustedSites и UntrustedSites см. в разделе [как: Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>См. также

- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Предоставить доверие к документам](../vsto/granting-trust-to-documents.md)
- [Устранение неполадок с безопасностью решений Office](../vsto/troubleshooting-office-solution-security.md)
- [Рекомендации по обеспечению безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md)