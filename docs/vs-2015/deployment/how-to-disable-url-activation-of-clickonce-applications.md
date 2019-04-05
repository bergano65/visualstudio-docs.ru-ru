---
title: Практическое руководство. Отключение активации ClickOnce-приложений по URL-адрес | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c22128d20bf83a8c6f2295b79653eabb3439c4b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993554"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Практическое руководство. Отключение активации по URL-адресу приложений ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Как правило, приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] запускается автоматически сразу после установки с веб-сервера. По соображениям безопасности можно отключить это поведение и сообщить пользователям, что запускать приложение нужно из меню **Пуск**. Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], установленных на компьютере пользователя с веб-сервера. Этот метод нельзя использовать для приложений, предназначенных только для использования в Интернете, запустить которые можно только с помощью URL. Дополнительные сведения о различиях между приложениями для использования только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется инструмент в составе [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe. Дополнительные сведения об этом инструменте см. в разделе [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Кроме того, эту процедуру можно выполнить с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL  
  
1.  Откройте манифест развертывания в MageUI.exe. Если еще не создана, выполните действия, описанные в [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Перейдите на вкладку **Параметры развертывания**.  
  
3.  Снимите флажок **Автоматически запускать приложение после установки**.  
  
4.  Сохраните и подпишите манифест.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
