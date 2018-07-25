---
title: Преимущество WhiteSource Bolt | Документация Майкрософт
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Сведения об активации учебной подписки WhiteSource Bolt, входящей в вашу подписку Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 37b71d51a62ab83f604c084ec2b5a1fda7594c14
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280318"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt в подписках Visual Studio

Находите и исправляйте уязвимости в продуктах с открытым исходным кодом и создавайте подробные отчеты об инвентаризации и лицензиях по всем компонентам с открытым исходным кодом в вашей сборке. Некоторые подписки Visual Studio предусматривают шесть месяцев бесплатного доступа.

## <a name="activation-steps"></a>Процедура активации

1.  Чтобы активировать преимущество WhiteSource Bolt, выполните вход на странице [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2.  Найдите плитку "WhiteSource Bolt" в разделе "Средства" и щелкните ссылку **Получить код** в нижней части плитки преимущества.

    ![Плитка преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Вы получите уведомления с кодом активации.  **Скопируйте код в буфер обмена**, а затем нажмите кнопку **Активировать**.

    ![Код преимущества WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  На веб-странице WhiteSource нажмите кнопку **Активировать** или прокрутите вниз до раздела **Activate your account** (Активация учетной записи) на странице.

    ![Активация преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  В разделе **Activate your account** (Активация учетной записи) страницы вам нужно будет выполнить четыре шага:

    - [Установите](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) расширение WhiteSource Bolt из Microsoft Visual Studio Marketplace. При отсутствии разрешений на установку расширений см. раздел [Установка бесплатных расширений для VSTS](/vsts/marketplace/install-vsts-extension?view=vsts).

    Нажмите зеленую кнопку **Установить**, если вы используете VSTS, или кнопку **Скачать** для Team Foundation Server.  В этом примере мы будем использовать VSTS.

    ![Установка расширения для преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-download-install.png)

    - Затем выберите нужную учетную запись VSTS и нажмите кнопку **Подтверждение**.  (Если VSTS еще не настроен, посетите страницу [Преимущества](https://my.visualstudio.com/benefits) и активируйте ваше преимущество VSTS.)

    ![Учетная запись для подтверждения преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - Вы получите подтверждение о том, что расширение установлено и готово к использованию.  Нажмите кнопку **Начать работу**, чтобы вернуться на страницу WhiteSource Bolt и продолжить работу.

    ![Установка преимущества WhiteSource завершена](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Откройте панель мониторинга проекта Visual Studio Team Services (VSTS), щелкните меню **Сборка и выпуск** и выберите **WhiteSource Bolt**.

    ![Добавление расширения для преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Вставьте код активации из плитки преимущества WhiteSource Bolt и нажмите кнопку **Активировать**. Каждый из кодов активации можно использовать для активации только одного проекта.

    ![Код активации преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Активация успешно завершена. На вашей подписке осталось 180 дней.

8.  В рамках сборки вам потребуется добавить расширение WhiteSource Bolt.  На [странице WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) опубликовано поясняющее видео.

9. После запуска сборки автоматически создаются следующие подробные отчеты и панели мониторинга:
    - Панель мониторинга уязвимостей системы безопасности
    - Отчет об уязвимостях системы безопасности
    - Отчет об устаревших библиотеках
    - Панель мониторинга рисков и обеспечения соответствия для лицензий
    - Отчет об инвентаризации

## <a name="eligibility"></a>Право на участие

| Уровень подписки                                                 |     Каналы                                            | Преимущество                                                          | Возможность возобновления    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (стандартная, годовая облачная)   | Корпоративная лицензия, Azure, розничная версия, некоторые версии не для перепродажи <sup>1</sup> | 6 месяцев       |  Да          |
| Visual Studio Professional (стандартная, годовая облачная) | Корпоративная лицензия, Azure, розничная версия                                       | Недоступно                                                           |Н/Д         |
| Visual Studio Test Professional (стандартная)                         | Корпоративная лицензия, розничная версия                                              | Недоступно                                             |  Н/Д         |
| MSDN Platforms (стандартная)                                          | Корпоративная лицензия, розничная версия                                              | Недоступно                                              | Н/Д         |
| Visual Studio Dev Essentials | Н/Д  | Недоступно |Н/Д |
| Visual Studio Enterprise, Visual Studio Professional (ежемесячная облачная) | Azure                                       | Недоступно                                                           |Н/Д|

<sup>1</sup> *Включает следующую категорию: Microsoft Partner Network (Enterprise).  Не включает следующие категории: прочие не для перепродажи (NFR), отраслевой партнер Visual Studio (VSIP), FTE, разработчик ПО и служб MCT, BizSpark, Imagine, Microsoft Valued Partner (MVP), региональный директор (RD), ПО и службы MCT, Microsoft Partner Network (Professional).*

Что делать, если вы не знаете свой уровень подписки?  Подключитесь к [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) для просмотра всех подписок, назначенных вашему адресу электронной почты. Если на этой странице отображаются не все подписки, возможно, часть из них назначена другому адресу электронной почты.  Чтобы увидеть их, войдите с соответствующим адресом электронной почты.

## <a name="support-resources"></a>Ресурсы поддержки

-  Нужна помощь с WhiteSource Bolt?  Вы можете начать беседу с представителем WhiteSource Bolt на странице https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  По вопросам продаж, использования подписок, учетных записей и выставления счетов для подписок Visual Studio обратитесь в [службу поддержки подписок](https://visualstudio.microsoft.com/subscriptions/support/) Visual Studio.
-  У вас есть вопросы о Visual Studio IDE, Visual Studio Team Services, других продуктах или службах Visual Studio?  Перейдите на [страницу поддержки Visual Studio](https://visualstudio.microsoft.com/support/).