---
title: 'Практическое: отключение активации ClickOnce-приложений по URL-адрес с помощью конструктора | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 6cc5571dffba9daa3ac1f5f78e354487cbc654fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562436"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Практическое руководство. Отключение активации ClickOnce-приложений по URL-адресу при помощи конструктора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: отключить URL-адрес активации из приложения ClickOnce с помощью конструктора](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer).  
  
Как правило [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения будет запускаться автоматически сразу после его установки на веб-сервере. По соображениям безопасности можно отключить это поведение и сообщить пользователям, чтобы запустить приложение из **запустить** меню вместо этого. Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], установленных на компьютере пользователя с веб-сервера. Он не может использоваться для интерактивных приложений, которые могут быть запущены только с помощью URL-адрес. Дополнительные сведения о различиях между только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Кроме того, эту задачу можно решить с помощью [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Дополнительные сведения см. в разделе [как: отключение активации из URL-АДРЕСУ приложений ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL  
  
1.  Щелкните правой кнопкой мыши имя проекта в **обозревателе решений**и нажмите кнопку **свойства**.  
  
2.  На **свойства** щелкните **публикации** вкладки.  
  
3.  Щелкните **Параметры**.  
  
4.  Нажмите кнопку **манифесты**.  
  
5.  Выберите флажок **Блокировать активацию с помощью URL-адреса приложения с**.  
  
6.  Развертывание приложения.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)



