---
title: "Преимущество WhiteSource Bolt | Документация Майкрософт"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/11/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: fe8e731e26765ec17b56383e04362efa25b2f141
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt в подписках Visual Studio

## <a name="overview"></a>Обзор

Находите и исправляйте уязвимости в продуктах с открытым исходным кодом и создавайте подробные отчеты об инвентаризации и лицензиях по всем компонентам с открытым исходным кодом в вашей сборке.  Некоторые подписки Visual Studio предусматривают 6 месяцев бесплатного доступа. 

## <a name="eligibility"></a>Право на участие

| Уровень подписки или программа                                                  | Преимущество               | Возможность возобновления                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise — уровень "Стандартный"                                             | 6 месяцев              | Да                                                                |
| Visual Studio Enterprise — годовая подписка                                               | 6 месяцев              | Да                                                                |
| Visual Studio Enterprise — месячная подписка                                              | Недоступно         |                                                                    |
| Visual Studio Professional — уровень "Стандартный"                                           | Недоступно         |                                                                    |
| Visual Studio Professional — годовая подписка                                             | Недоступно         |                                                                    | 
| Visual Studio Professional — месячная подписка                                            | Недоступно         |                                                                    |
| Visual Studio Test Pro                                                        | Недоступно         |                                                                    |
| MSDN Platforms                                                                | Недоступно         |                                                                    |
| Visual Studio Dev Essentials                                                  | Недоступно         |                                                                    |
| Visual Studio Enterprise — NFR<sup>1</sup>                                               | Недоступно         |                                                                    |
| Visual Studio Enterprise — FTE                                                | Недоступно         |                                                                    |
| Visual Studio Enterprise — Microsoft Partner Network                          | 6 месяцев              | Да                                                                |
| Visual Studio Professional — Microsoft Partner Network                        | Недоступно         |                                                                    |
| Visual Studio Enterprise — Imagine (уровень "Стандартный")                                 | Недоступно         |                                                                    |
| Visual Studio Enterprise — Imagine (уровень "Премиум")                                  | Недоступно         |                                                                    |
| Visual Studio Enterprise — BizSpark                                           | Недоступно         |                                                                    |
| Microsoft Certified Trainer — программное обеспечение и службы                             | Недоступно         |                                                                    |
| Microsoft Certified Trainer — разработчик программного обеспечения и служб                   | Недоступно         |                                                                    |

<sup>1</sup> *Включает категории членства NFR (не для перепродажи), MVP (ценный партнер корпорации Майкрософт), RD (директор региона), VSIP (отраслевой партнер Visual Studio)*   

Что делать, если вы не знаете свой уровень подписки?  Перейдите на страницу [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs), чтобы увидеть все подписки, назначенные вашему адресу электронной почты. Если на этой странице отображаются не все подписки, возможно, часть из них назначена другому адресу электронной почты.  Чтобы увидеть их, войдите с соответствующим адресом электронной почты. 

## <a name="activation-steps"></a>Процедура активации

1.  Чтобы воспользоваться преимуществом WhiteSource Bolt, перейдите по адресу [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2.  Найдите плитку "WhiteSource Bolt" в разделе "Средства" и щелкните ссылку **Получить код** в нижней части плитки преимущества.    

    ![Плитка преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Вы получите уведомления с кодом активации.  **Скопируйте код в буфер обмена**, а затем нажмите кнопку **Активировать**. 

    ![Код преимущества WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  На веб-странице WhiteSource нажмите кнопку **Активировать** или прокрутите вниз до раздела **Activate your account** (Активация учетной записи) на странице.  

    ![Активация преимущества WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  В разделе **Activate your account** (Активация учетной записи) страницы вам нужно будет выполнить четыре шага:
    - [Установите](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) расширение WhiteSource Bolt из Microsoft Visual Studio Marketplace. При отсутствии разрешений на установку расширений посетите [эту страницу](https://www.visualstudio.com/docs/marketplace/get-vsts-extensions#request).

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

## <a name="faq"></a>часто задаваемые вопросы
*Проверка обновлений*

## <a name="support-resources"></a>Ресурсы поддержки
-  Нужна помощь с WhiteSource Bolt?  Начните интерактивный чат представителем службы WhiteSource Bolt на странице https://www.whitesourcesoftware.com/vse_whitesource_bolt/. 
-  По вопросам продаж, использования подписок, учетных записей и выставления счетов для подписок Visual Studio обратитесь в [службу поддержки подписок](https://www.visualstudio.com/subscriptions/support/) Visual Studio.
-  У вас есть вопросы о Visual Studio IDE, Visual Studio Team Services, других продуктах или службах Visual Studio?  Перейдите на [страницу поддержки Visual Studio](https://www.visualstudio.com/support/). 

