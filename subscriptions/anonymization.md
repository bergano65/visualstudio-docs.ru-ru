---
title: Анонимизация данных подписчика Visual Studio | Документация Майкрософт
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Сведения о том, как анонимизируются данные подписчика при потере доступа к подпискам.
ms.openlocfilehash: d15fce8d5e1a64066a42cea69b770f55c9607f06
ms.sourcegitcommit: 02acadb912faced7eaffe27c2c19104bf0428bcd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936914"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Анонимизация данных подписчика Visual Studio
При возникновении события, блокирующего подписчику возможность пользования подпиской, например при истечении срока действия подписки или удалении учетной записи для входа подписчика, персональные данные пользователя, такие как имя и учетная запись для входа, шифруются, чтобы сделать их непригодными к использованию.  Это позволяет защитить персональные данные подписчика.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Когда происходит анонимизация?
События, делающие подписку непригодной к использованию подписчиком, активируют анонимизацию.  Скорость анонимизации зависит от активировавшего ее события и типа подписки. Дополнительные сведения см. в таблице ниже.

| Тип подписки                                                                                                                       | Событие, активирующее анонимизацию                                                                                                     | Когда происходит анонимизация |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Подписчик явно отказывается от участия в программе или не принимает условия использования                                    | 30 дней               |
| Подписки Visual Studio, приобретенные через Microsoft Store (в розницу)                                                                      | Подписка не активирована, или истекает срок ее действия                                                                   | 360 дней                  |
| Подписки Visual Studio, приобретенной по корпоративной лицензии, в Visual Studio Marketplace (облачные подписки) или по таким программам, как MPN | Подписка не назначена пользователю, или истекает срок ее действия                                                          | 180 дней                  |
| Все подписки                                                                                                                       | Учетная запись Azure Active Directory или учетная запись Майкрософт (MSA), используемая для входа в подписку, закрыта | Немедленно               |
| Все подписки                                                                                                                       | Подписчик удаляется из клиента, который связан с данной учетной записью Azure Active Directory                                | Немедленно               |

## <a name="faq"></a>часто задаваемые вопросы
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Вопрос:  Теряет ли подписчик доступ к своей подписке при анонимизации его персональных данных?
Ответ.  Нет.  Анонимизация является реакцией на событие, приводящее к потере доступа к подписке, но не ограничивает такой доступ.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Вопрос:  Я являюсь администратором по подпискам организации.  Если данные одного из моих подписчиков анонимизированы, можно ли переназначить эту подписку другому пользователю?
Ответ.  Да, если срок действия подписки не истек, ее можно переназначить другому подписчику.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Вопрос: Как предотвратить анонимизацию из-за удаления адреса электронной почты для входа?
Ответ.  Предотвратить эту проблему можно двумя способами:
- Развертывание системы управления с одним удостоверением — MSA или AAD (но не обоими).  
- Сопоставление удостоверений AAD и MSA через клиент. 

## <a name="next-steps"></a>Следующие шаги
Сведения о запрете анонимизации посредством [связывания удостоверений MSA и AAD](/azure/active-directory/b2b/add-users-administrator).
