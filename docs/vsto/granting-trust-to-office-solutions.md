---
title: Предоставление доверия решениям Office
description: Чтобы предоставить доверие для решений Office, можно изменить политику безопасности каждого целевого компьютера, чтобы она доверяла сборке решения, манифесту развертывания и документу.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f98f3154a0708ce7a01603968f0f5774dd86f40e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910228"
---
# <a name="grant-trust-to-office-solutions"></a>Предоставление доверия решениям Office
  Предоставление доверия для решений Office означает изменение политики безопасности каждого целевого компьютера на доверие к сборке решения, манифесту приложения, манифесту развертывания и документу. Решение Office может быть предоставлено вам или конечному пользователю.

 Можно предоставить полное доверие для решения Office, подписывая манифесты приложения и развертывания.

 Конечные пользователи могут предоставить доверие для решения Office, принимая решение о доверии в [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запросе о доверии.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Доверять решению, подписывая манифесты приложения и развертывания
 Все манифесты приложения и развертывания для решений Office должны быть подписаны сертификатом, идентифицирующим издателя. Сертификаты предоставляют базу для принятия решений о доверии.

 Временный сертификат создается для вас и предоставляется доверие во время сборки, поэтому решение будет выполняться во время его отладки. При публикации решения, подписанного временным сертификатом, конечному пользователю будет предложено принять решение о доверии.

 Если вы подписываете решение с помощью известного и доверенного сертификата, решение будет автоматически установлено без запроса конечного пользователя принять решение о доверии. Дополнительные сведения о том, как получить сертификат для подписания, см. в разделе [ClickOnce и Authenticode](../deployment/clickonce-and-authenticode.md). После получения сертификата сертификат должен быть явно доверенным, добавив его в список доверенных издателей. Дополнительные сведения см. в разделе [как добавить доверенный издатель на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Если разработчик подписывает решение с временным сертификатом, администратор может повторно подписать настройку с помощью известного и доверенного сертификата, используя Инструмент создания и изменения манифестов (*mage.exe*), который является одним из инструментов Microsoft .NET Framework. Дополнительные сведения о подписывании решений см. в статьях [как подписать решения Office](../vsto/how-to-sign-office-solutions.md) и [как подписать манифесты приложения и развертывания](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Доверие к решению с помощью запроса о доверии ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] предлагает пользователю принять решение о доверии, если не существует политики Организации, которая доверяет сертификату решения. Если конечный пользователь предоставляет доверие для решения, создается запись списка включения, содержащая URL-адрес и открытый ключ для сохранения этого решения о доверии. Когда надежная настройка выполняется позже, конечный пользователь не запрашивается снова.

 Администраторы могут отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запрос о доверии или потребовать, чтобы запрос выполнялся только для решений, подписанных с помощью сертификата Authenticode. Дополнительные сведения о том, как изменить эти параметры для зон MyComputer, LocalIntranet, Internet, Трустедситес и Унтрустедситес, см. [в разделе как настроить поведение запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>См. также раздел

- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Предоставление доверия документам](../vsto/granting-trust-to-documents.md)
- [Устранение неполадок в системе безопасности решений Office](../vsto/troubleshooting-office-solution-security.md)
- [Конкретные вопросы безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md)