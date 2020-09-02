---
title: Инструкции. Отключение активации URL-адресов приложений ClickOnce с помощью конструктора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153815"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Практическое руководство. Отключение активации ClickOnce-приложений по URL-адресу при помощи конструктора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Как правило, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение запустится автоматически сразу после установки с веб-сервера. По соображениям безопасности вы можете отключить это поведение и сообщить пользователям о необходимости запуска приложения из меню " **Пуск** ". Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], установленных на компьютере пользователя с веб-сервера. Его нельзя использовать для интерактивных приложений, которые могут запускаться только с помощью URL-адреса. Дополнительные сведения о разнице между приложениями, работающими только в сети, и установленных приложениях см. [в разделе Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Эту задачу также можно выполнить с помощью [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Дополнительные сведения см. [в разделе инструкции. Отключение активации URL-адресов для приложений ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL  
  
1. Щелкните правой кнопкой мыши имя проекта в **Обозреватель решений**и выберите пункт **свойства**.  
  
2. На странице **Свойства** перейдите на вкладку **Публикация** .  
  
3. Щелкните **Параметры**.  
  
4. Щелкните **манифесты**.  
  
5. Установите флажок **Блокировать активацию приложения с помощью URL-адреса**.  
  
6. Разверните приложение.  
  
## <a name="see-also"></a>См. также:  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
