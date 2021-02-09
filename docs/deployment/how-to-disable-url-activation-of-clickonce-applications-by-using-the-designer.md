---
title: Отключение активации URL-адресов для приложений ClickOnce с помощью конструктора
description: Узнайте, как отключить автоматический запуск при установке для приложения ClickOnce с помощью Visual Studio, чтобы пользователи должны запустить приложение из меню "Пуск".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 520f9aea1dbd3d3f742293a95b4dd7bdbac62a3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900764"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Практическое руководство. Отключение активации приложений ClickOnce по URL-адресу с помощью конструктора
Как правило, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение запустится автоматически сразу после установки с веб-сервера. По соображениям безопасности вы можете отключить это поведение и сообщить пользователям о необходимости запуска приложения из меню " **Пуск** ". Следующая процедура описывает процесс отключения активации через URL.

 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установленных на компьютере пользователя с веб-сервера. Его нельзя использовать для интерактивных приложений, которые могут запускаться только с помощью URL-адреса. Дополнительные сведения о разнице между приложениями, работающими только в сети, и установленных приложениях см. [в разделе Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 В этой процедуре используется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Эту задачу также можно выполнить с помощью [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Дополнительные сведения см. [в разделе инструкции. Отключение активации URL-адресов для приложений ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Процедура

#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL

1. Щелкните правой кнопкой мыши имя проекта в **Обозреватель решений** и выберите пункт **свойства**.

2. На странице **Свойства** перейдите на вкладку **Публикация** .

3. Щелкните **Параметры**.

4. Щелкните **манифесты**.

5. Установите флажок **Блокировать активацию приложения с помощью URL-адреса**.

6. Разверните приложение.

## <a name="see-also"></a>См. также раздел
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)