---
title: Преимущество WhiteSource Bolt | Документация Майкрософт
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: Get-Started-Article
description: Сведения об активации учебной подписки WhiteSource Bolt, входящей в вашу подписку Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4169036161e19092a78133207261f2fe434c1316
ms.sourcegitcommit: 8c4267540c0ac39664f6902c423516f408f3cbd4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2019
ms.locfileid: "54380022"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt в подписках Visual Studio

Находите и исправляйте уязвимости в продуктах с открытым исходным кодом и создавайте подробные отчеты об инвентаризации и лицензиях по всем компонентам с открытым исходным кодом в вашей сборке. Некоторые подписки Visual Studio предусматривают шесть месяцев бесплатного доступа.

## <a name="activation-steps"></a>Процедура активации

1. Чтобы активировать преимущество WhiteSource Bolt, выполните вход на странице [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2. Найдите плитку "WhiteSource Bolt" в разделе "Средства" и щелкните ссылку **Получить код** в нижней части плитки преимущества.
   > [!div class="mx-imgBorder"]
   > ![Плитка преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-tile.png)

3. Вы получите уведомления с кодом активации.  **Скопируйте код в буфер обмена**, а затем нажмите кнопку **Активировать**.
   > [!div class="mx-imgBorder"]
   > ![Код преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-code.png)

4. На веб-странице WhiteSource нажмите кнопку **Активировать** или прокрутите вниз до раздела **Activate your account** (Активация учетной записи) на странице.
   > [!div class="mx-imgBorder"]
   > ![Активация преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. В разделе **Activate your account** (Активация учетной записи) страницы вам нужно будет выполнить четыре шага:

   - [Установите](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) расширение WhiteSource Bolt из Microsoft Visual Studio Marketplace. При отсутствии разрешений на установку расширений см. раздел [Установка бесплатных расширений для Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts).


Нажмите зеленую кнопку **Установить**, если вы используете Azure DevOps Services, или кнопку **Загрузить** для Team Foundation Server.  В этом примере мы будем использовать Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![Установка расширения для преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-download-install.png)

- Затем выберите нужную организацию Azure DevOps и нажмите кнопку **Подтвердить**.  (Если вы еще не настроили Azure DevOps Services, посетите страницу [Преимущества](https://my.visualstudio.com/benefits) и активируйте преимущество Azure DevOps Services.)

> [!div class="mx-imgBorder"]
> ![Учетная запись для подтверждения преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-confirm-account.png)

- Вы получите подтверждение о том, что расширение установлено и готово к использованию.  Нажмите кнопку **Начать работу**, чтобы вернуться на страницу WhiteSource Bolt и продолжить работу.
> [!div class="mx-imgBorder"]
> ![Установка преимущества WhiteSource завершена](_img/vs-whitesource/vs-whitesource-install-complete.png)

5. Откройте панель мониторинга проекта Azure DevOps, откройте меню **Azure Pipelines** и выберите **WhiteSource Bolt**.
   > [!div class="mx-imgBorder"]
   > ![Добавление расширения для преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Вставьте код активации из плитки преимущества WhiteSource Bolt и нажмите кнопку **Активировать**. Каждый из кодов активации можно использовать для активации только одного проекта.
   > [!div class="mx-imgBorder"]
   > ![Код активации преимущества WhiteSource](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. Активация успешно завершена. На вашей подписке осталось 180 дней.

8. В рамках сборки вам потребуется добавить расширение WhiteSource Bolt.  На [странице WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) опубликовано поясняющее видео.

9. После запуска сборки автоматически создаются следующие подробные отчеты и панели мониторинга:
    - Панель мониторинга уязвимостей системы безопасности
    - Отчет об уязвимостях системы безопасности
    - Отчет об устаревших библиотеках
    - Панель мониторинга рисков и обеспечения соответствия для лицензий
    - Отчет об инвентаризации

## <a name="eligibility"></a>Право на участие

| Уровень подписки                                                 |     Каналы                                            | Преимущество                                                          | Возможность возобновления    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (ценовая категория "Стандартный")   | Корпоративная лицензия, Azure, розничная версия, некоторые версии не для перепродажи <sup>1</sup> | 6 месяцев       |  Да          |
| Visual Studio Professional (ценовая категория "Стандартный") | Корпоративная лицензия, Azure, розничная версия                                       | Недоступно                                                           |Н/Д         |
| Visual Studio Test Professional (стандартная)                         | Корпоративная лицензия, розничная версия                                              | Недоступно                                             |  Н/Д         |
| MSDN Platforms (стандартная)                                          | Корпоративная лицензия, розничная версия                                              | Недоступно                                              | Н/Д         |
| Visual Studio Dev Essentials | Н/Д  | Недоступно |Н/Д |
| Visual Studio Enterprise, Visual Studio Professional (ежемесячная облачная) | Azure                                       | Недоступно                                                           |Н/Д|

<sup>1</sup> *Включает следующие категории:  Microsoft Partner Network (Enterprise).  Не включает следующие категории: прочие не для перепродажи (NFR), отраслевой партнер Visual Studio (VSIP), FTE, разработчик ПО и служб MCT, BizSpark, Imagine, Most Valuable Professional (MVP), региональный директор (RD), ПО и службы MCT, Microsoft Partner Network (Professional).*


> [!NOTE]
> Корпорация Майкрософт больше не предлагает годовые подписки на Visual Studio Professional и Visual Studio Enterprise в рамках облачных подписок. Никаких изменений не предвидится в том, что существующие клиенты могут продлить, изменить или отменить свои подписки. Новым клиентам мы рекомендуем ознакомиться с расценками на Visual Studio и вариантами покупки на этой странице: [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/).


Что делать, если вы не знаете свой уровень подписки?  Подключитесь к [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) для просмотра всех подписок, назначенных вашему адресу электронной почты. Если на этой странице отображаются не все подписки, возможно, часть из них назначена другому адресу электронной почты.  Чтобы увидеть их, войдите с соответствующим адресом электронной почты.

## <a name="support-resources"></a>Ресурсы поддержки

-  Нужна помощь с WhiteSource Bolt?  Вы можете начать беседу с представителем WhiteSource Bolt на странице https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  По вопросам продаж, использования подписок, учетных записей и выставления счетов для подписок Visual Studio обратитесь в [службу поддержки подписок](https://visualstudio.microsoft.com/subscriptions/support/) Visual Studio.
-  У вас есть вопросы о Visual Studio IDE, Azure DevOps Services или других продуктах или службах Visual Studio?  Перейдите на [страницу поддержки Visual Studio](https://visualstudio.microsoft.com/support/).