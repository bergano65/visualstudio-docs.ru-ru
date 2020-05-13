---
title: Доверие к решениям Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301659"
---
# <a name="grant-trust-to-office-solutions"></a>Доверие к решениям Office
  Доверие к решениям Office означает изменение политики безопасности каждого целевого компьютера, чтобы доверять сборке решений, манифесту приложений, манифесту развертывания и документу. Доверие может быть предоставлено решению Office либо вами, либо конечным пользователем.

 Вы можете полностью доверять решению Office, подписав манифесты приложения и развертывания.

 Конечные пользователи могут доверять решению Office, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] прими доверительное решение в доверии.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Доверяйте решению, подписывая манифесты приложения и развертывания
 Все манифесты приложений и развертывания для решений Office должны быть подписаны сертификатом, идентифицируя издателя. Сертификаты являются основой для принятия доверительных решений.

 Временный сертификат создан для вас и предоставлено доверие во время сборки, так что решение будет работать в то время как вы отладить его. Если вы опубликуете решение, подписанное временным сертификатом, конечному пользователю будет предложено принять решение о доверии.

 Если вы подпишете решение с известным и надежным сертификатом, решение будет автоматически установлено, не побуждая конечному пользователю принять решение о доверии. Для получения дополнительной информации о том, как получить сертификат для подписания, [см.](../deployment/clickonce-and-authenticode.md) После получения сертификата сертификату необходимо явно доверять, добавляя его в список доверенных издателей. Для получения дополнительной информации см. [Как: Добавить доверенного издателя на клиентский компьютер для clickOnce приложений](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Если разработчик подписывает решение временным сертификатом, администратор может повторно подписать настройку с известным и надежным сертификатом, используя инструмент manifest Generation and Editing Tool *(mage.exe),* который является одним из инструментов Microsoft .NET Framework. Для получения дополнительной информации о решениях для [How to: Sign application and deployment manifests](../ide/how-to-sign-application-and-deployment-manifests.md)подписания [см.](../vsto/how-to-sign-office-solutions.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Доверяйте решению, используя подсказку доверия ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]побуждает конечный пользователь принять решение о доверии, если нет общеорганизационных политики, которая доверяет сертификату решения. Если конечный пользователь доверяет решению, создается запись списка включений, содержащая URL и открытый ключ для хранения этого решения о доверии. При повторной настройке доверенная настройка не подсказывается снова.

 Администраторы могут отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запрос доверия или потребовать, чтобы запрос возник только для решений, подписанных сертификатом Authenticode. Для получения дополнительной информации о том, как изменить эти настройки для MyComputer, LocalInnet, Интернет, TrustedSites, и untrustedSites зон, [см.](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)

## <a name="see-also"></a>См. также раздел

- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Грант доверие к документам](../vsto/granting-trust-to-documents.md)
- [Безопасность решения для устранения неполадок Office](../vsto/troubleshooting-office-solution-security.md)
- [Конкретные соображения безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md)