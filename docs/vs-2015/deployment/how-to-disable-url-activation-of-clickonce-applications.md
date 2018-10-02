---
title: 'Практическое: отключение активации ClickOnce-приложений по URL-адрес | Документация Майкрософт'
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
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ad43abbafe1d5f70bb2de748154a0066aa3d8927
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561199"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Практическое руководство. Отключение активации по URL-адресу приложений ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: отключение активации из URL-АДРЕСУ приложений ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications).  
  
Как правило, приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] запускается автоматически сразу после установки с веб-сервера. По соображениям безопасности можно отключить это поведение и сообщить пользователям, чтобы запустить приложение из **запустить** меню вместо этого. Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], установленных на компьютере пользователя с веб-сервера. Этот метод нельзя использовать для приложений, предназначенных только для использования в Интернете, запустить которые можно только с помощью URL. Дополнительные сведения о различиях между интерактивными и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется инструмент в составе [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe. Дополнительные сведения об этом инструменте см. в разделе [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Кроме того, эту процедуру можно выполнить с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL  
  
1.  Откройте манифест развертывания в MageUI.exe. Если еще не создана, выполните действия, описанные в [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Выберите **варианты развертывания** вкладки.  
  
3.  Очистить **автоматически запускать приложение после установки** "флажок".  
  
4.  Сохраните и подпишите манифест.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)



