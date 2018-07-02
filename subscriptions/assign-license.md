---
title: Назначение лицензий для подписок Visual Studio | Документы Майкрософт
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Сведения о том, как администраторы могут назначать лицензии для подписчиков.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4325921bbaa75e0fb8a8a16947c45901b6f01649
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477383"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Назначение лицензий на портале администратора подписок Visual Studio

Администраторы подписок Visual Studio могут использовать портал администратора подписок Visual Studio для назначения подписок отдельным пользователям.  
Можно назначать по одной подписке или использовать функцию "пакетного добавления" для быстрой загрузки списков подписчиков с информацией об их подписках. 

## <a name="assigning-a-single-user"></a>Назначение одному пользователю
При наличии доступных лицензий для подписок Visual Studio вы можете назначить их новым пользователям, чтобы предоставить им доступ к преимуществам подписки. 
1.  Войдите на [портал администратора](https://manage.visualstudio.com)

2.  Чтобы назначить одного подписчика Visual Studio, в верхней части таблицы нажмите кнопку **Добавить**.

    <img alt="Add subscriber" src="_img\assign-license-add\assign-license-add.png" style="border: 1px solid #CCCCCC" />

3.  Введите сведения в поля формы для нового подписчика. Если ваша организация использует Azure Active Directory, это поле действует как функция поиска людей в текущем каталоге, позволяя выбрать подходящего пользователя в результатах поиска. Когда вы выберете нужного человека, его имя, адрес электронной почты для входа и адрес для уведомлений будут заполнены автоматически, как показано ниже. 

    Если в вашей организации не используется Azure Active Directory (Azure AD), но используются разные адреса электронной почты для приема сообщений и входа в систему, здесь вы сможете ввести нужный адрес. Выберите ссылку с надписью "Add a different email for receiving communication" (Добавить другой адрес электронной почты для получения сообщений). 

    **Доступ к скачиванию:**  
    Если требуется предоставить подписчику доступ к скачиванию программного обеспечения при входе на [портал управления подписками Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), переключатель параметра "Скачивания" должен быть включен. Если отключить параметр скачиваний, пользователь не будет иметь доступ к скачиваемым файлам, но сохранит доступ ко всем другим преимуществам подписки. 
    
    Завершив выбор параметров для подписчика, нажмите кнопку **Добавить**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  После добавления подписчика ему автоматически отправляется сообщение электронной почты о назначении, содержащее дальнейшие инструкции. Сообщение о назначении можно переотправить в любое время, выбрав подписчика и нажав кнопку **Отправить заново** в верхнем меню.

    <img alt="Subscriber added" src="_img\assign-license-add\add-subscriber-complete.png" style="border: 1px solid #CCCCCC" />

## <a name="bulk-assignments"></a>Массовые назначения
1.  Чтобы добавить сразу несколько подписчиков, откройте вкладку **управления подписчиками**. На ленте в верхней части нажмите кнопку **Массовое добавление**. 

    <img alt="Bulk add" src="_img\assign-license-add\bulk-assign-add.png" style="border: 1px solid #CCCCCC" />

2. Массовое назначение использует шаблон Microsoft Excel для отправки подписчиков. В диалоговом окне "Upload Multiple Subscribers" (Отправка нескольких подписчиков) нажмите кнопку **Скачать**, чтобы скачать этот шаблон. Всегда скачивайте последнюю версию шаблона. При использовании более старой версии массовая отправка может завершиться ошибкой.

    <img alt="Upload multiple subscribers" src="_img\assign-license-add\bulk-assign-upload.png" style="border: 1px solid #CCCCCC" />

3.  В таблице Excel заполните поля сведениями о людях, которым вы хотите назначить подписки. Поле "Ссылка" является необязательным. Если вы неправильно заполнили какую-либо часть шаблона, отображается сообщение об ошибке с описанием проблемы. По завершении сохраните файл в локальном расположении.
**Чтобы обеспечить правильную отправку, соблюдайте следующие рекомендации:**
    - Проследите за тем, чтобы ни одно из полей формы не содержало запятые.
    - Удалите пробелы до и после полей формы, например имен пользователей.
    - Убедитесь, что имена и фамилии пользователей, состоящие из двух частей, не содержат лишние пробелы (например, имя "Maggie May" не следует вводить как "Maggie  May", так как система не удалит лишний пробел).
    <img alt="Bulk add template" src="_img\assign-license-add\bulk-template.png" style="border: 1px solid #CCCCCC" />

4.  Вернитесь на портал администрирования подписок Visual Studio и нажмите кнопку **Обзор** в диалоговом окне "Отправка нескольких подписчиков". Перейдите к сохраненному файлу Excel и нажмите кнопку **ОК**. На экране отображается индикатор хода отправки. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Если шаблон содержит ошибки, отправка завершается сбоем и отображаются соответствующие ошибки, чтобы можно было исправить шаблон и повторить попытку.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Если отправка выполнена успешно, отображается список подписчиков и сообщение с подтверждением.

   <img alt="Upload complete" src="_img\assign-license-add\bulk-assign-upload-complete.png" style="border: 1px solid #CCCCCC" />