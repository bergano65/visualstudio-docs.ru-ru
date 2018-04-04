---
title: Идентификаторы для подписчиков Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Идентификаторы для подписчиков Visual Studio

Когда вы активируете подписку Visual Studio, мы привязываем ваш идентификатор (или имя пользователя), использованный при активации, к подписке Visual Studio. Таким образом, мы узнаем вас на [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), в VSTS и в Azure.

В VSTS мы проверяем состояние вашей подписки Visual Studio при каждом входе и автоматически предоставляем вам возможности каждой учетной записи, членом которой вы являетесь. Поскольку эти возможности являются преимуществами подписчиков, вас можно бесплатно добавить в любую учетную запись VSTS с помощью идентификатора, привязанного к вашей подписке Visual Studio.

В Azure мы проверяем состояние вашей подписки Visual Studio при активации [ежемесячного кредита Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), который является преимуществом подписчиков.

На [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) вы можете добавить **альтернативный идентификатор** — помимо идентификатора, использованного при активации. В настоящий момент вы можете добавить альтернативный идентификатор, если вы использовали учетную запись Майкрософт для активации подписки. Таким образом, вы можете добавить рабочую или учебную учетную запись (которую вы используете при входе в Visual Studio, Office 365, сеть организации или школы), чтобы использовать VSTS через личную учетную запись, а также рабочую или учебную учетную запись.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Как добавить альтернативный идентификатор в подписку Visual Studio

1. Войдите на [портал подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Если вас попросят выбрать "личную учетную запись" или "рабочую или учебную учетную запись", выберите личную (вашу учетную запись Майкрософт).
  >
  > Иногда необходимо выбирать, поскольку в вашей учетной записи Майкрософт и в вашей рабочей или учебной учетной записи используется один адрес электронной почты. Хотя оба идентификатора привязаны к одному адресу электронной почты, они существуют раздельно и имеют разные профили, параметры безопасности и разрешения.
  >
  > С 30 марта 2018 года вы не сможете создавать учетную запись Майкрософт, указав адрес электронной почте на домене, который управляется в Azure Active Directory. Вы по-прежнему сможете входить в рабочую учетную запись с помощью этого адреса.

2. Перейдите на вкладку **Подписки**.

  ![Нажмите "Подписки"](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. В разделе **Связанные ссылки** выберите пункт **Добавить альтернативную учетную запись**.

  ![В разделе "Связанные ссылки" выберите пункт "Добавить альтернативную учетную запись"](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Введите рабочую или учебную учетную запись и нажмите **Добавить**.

  ![Введите рабочую или учебную учетную запись](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Войдите в учетную запись VSTS с рабочей или учебной учетной записью (```https://{youraccount}.visualstudio.com```). Передача информации может занять некоторое время, так что проверьте еще раз через 15 минут. 

## <a name="faq"></a>часто задаваемые вопросы

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Вопрос. Почему VSTS не распознает меня как подписчика Visual Studio?
Ответ. Служба VSTS должна автоматически распознавать вашу подписку при входе с основным или альтернативным идентификатором. Если этого не происходит, попробуйте выполнить следующее.

* Убедитесь, что у вас есть активная подписка Visual Studio, которая [включает VSTS в качестве преимущества](vs-vsts.md).

* Убедитесь, что выполнили вход с основным или альтернативным идентификатором для вашей подписки Visual Studio.

* Посетите [портал подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) по крайней мере один раз перед входом в VSTS.

Если VSTS по-прежнему не распознает вашу подписку, [обратитесь в службу поддержки](https://www.visualstudio.com/team-services/support/)

