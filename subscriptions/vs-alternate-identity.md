---
title: Идентификаторы для подписчиков Visual Studio
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 07/19/2019
ms.topic: conceptual
description: Как добавить альтернативный идентификатор для подписки Visual Studio, который будет использоваться для Azure DevOps и Azure
ms.openlocfilehash: ff5166da3cb782c0750b0ce61fdafec375811ff4
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232004"
---
# <a name="identities-for-visual-studio-subscribers"></a>Идентификаторы для подписчиков Visual Studio
Когда вы активируете подписку Visual Studio, мы привязываем ваш идентификатор (или имя пользователя), использованный при активации, к подписке Visual Studio. Таким образом мы сможем узнать вас на [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), в Azure DevOps и в Azure.

В Azure DevOps мы проверяем состояние вашей подписки Visual Studio при каждом входе и автоматически предоставляем вам возможности каждой организации, членом которой вы являетесь.
Так как эти возможности являются преимуществами подписчиков, вас можно бесплатно добавить в любую организацию Azure DevOps с помощью идентификатора, связанного с вашей подпиской Visual Studio.

В Azure мы проверяем состояние вашей подписки Visual Studio при активации [ежемесячного индивидуального кредита Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), который является преимуществом подписчиков.

На [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) вы можете добавить **альтернативный идентификатор** — помимо идентификатора, использованного при активации. Вы можете добавить альтернативный идентификатор, если вы использовали учетную запись Майкрософт для активации подписки. Таким образом, вы можете добавить рабочую или учебную учетную запись (которую вы используете при входе в Visual Studio, Office 365, сеть организации или школы), чтобы использовать Azure DevOps через личную учетную запись, а также рабочую или учебную учетную запись.

## <a name="add-an-alternate-account-to-your-subscription"></a>Добавление альтернативной учетной записи в подписку
Добавление альтернативной учетной записи в подписку Visual Studio позволяет получить доступ к преимуществам подписки, таким как Azure DevOps и Azure, с идентификатором, отличным от того, которому назначена подписка. В прошлом эта возможность была доступна, только если подписка Visual Studio была назначена учетной записи Майкрософт. Мы распространили ее на рабочие и учебные учетные записи в Azure Active Directory (Azure AD).

При этом копия подписки не предоставляет другой учетной записи. Вы лишь получаете возможность доступа к указанным преимуществам с помощью альтернативной учетной записи.

Для всех подписок можно добавить рабочую или учебную учетную запись, чтобы использовать ее с преимуществами, для которых требуется вход (IDE Visual Studio, Azure DevOps и Azure).

### <a name="add-the-alternate-account"></a>Добавление альтернативной учетной записи
1. Войдите на портал подписчика Visual Studio с помощью учетной записи Майкрософт (https://my.visualstudio.com).
2. Перейдите на вкладку **Подписки**.
3. Щелкните ссылку **Добавить альтернативную учетную запись**.
4. Добавьте рабочую или учебную учетную запись.
    > [!div class="mx-imgBorder"]
    > ![Добавление рабочей или учебной учетной записи](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Войдите в Azure DevOps, используя рабочую или учебную учетную запись (https://{ваша_учетная_запись}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Использование рабочей или учебной учетной записи](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Альтернативная учетная запись будет добавлена в подписку Visual Studio, что позволит использовать оба идентификатора для доступа к преимуществам подписки, для которых требуется вход с помощью альтернативной учетной записи (IDE, Azure DevOps и Azure).

## <a name="faq"></a>часто задаваемые вопросы

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Вопрос:  Почему Azure DevOps не распознает меня как подписчика Visual Studio?

Ответ. Служба Azure DevOps должна автоматически распознавать вашу подписку при входе с основным или альтернативным идентификатором. Если этого не происходит, попробуйте выполнить следующее.

* Убедитесь, что у вас есть активная подписка Visual Studio, которая включает [Azure DevOps](vs-azure-devops.md#eligibility) в качестве преимущества.

* Убедитесь, что выполнили вход с основным или альтернативным идентификатором для вашей подписки Visual Studio.

* Посетите [портал подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) по крайней мере один раз перед входом в Azure DevOps.

Если Azure DevOps по-прежнему не распознает вашу подписку, [обратитесь в службу поддержки Azure DevOps](https://azure.microsoft.com/support/devops/).

## <a name="see-also"></a>См. также
- [Документация по Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Документация по Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Документация по Azure](https://docs.microsoft.com/azure/)
- [Документация по Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Следующие шаги 
Дополнительные сведения об использовании Azure, Azure DevOps или интегрированной среды разработки Visual Studio см. в следующих ресурсах:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)