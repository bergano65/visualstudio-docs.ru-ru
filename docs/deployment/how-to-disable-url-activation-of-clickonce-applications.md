---
title: 'Как: отключение активации по URL-АДРЕСУ приложений ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 1d781736d53b4f0ff61b6007f3017554e60e0293
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Практическое руководство. Отключение активации по URL-адресу приложений ClickOnce
Как правило, приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запускается автоматически сразу после установки с веб-сервера. По соображениям безопасности можно отключить это поведение и сообщить пользователям, чтобы запустить приложение из **запустить** меню вместо него. Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установленных на компьютере пользователя с веб-сервера. Этот метод нельзя использовать для приложений, предназначенных только для использования в Интернете, запустить которые можно только с помощью URL. Дополнительные сведения о различиях между приложениями только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется [! ВКЛЮЧИТЬ[winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Кроме того, эту процедуру можно выполнить с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL  
  
1.  Откройте манифест развертывания в MageUI.exe. Если вы создали один, выполните действия в [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Выберите **варианты развертывания** вкладки.  
  
3.  Очистить **автоматически запускать приложение после установки** флажок.  
  
4.  Сохраните и подпишите манифест.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)