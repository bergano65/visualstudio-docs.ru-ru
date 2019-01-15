---
title: Как выполнить Отключение активации ClickOnce-приложений по URL-адрес | Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 611bb0d2c3c828be5f8eaa10f3baeaafca1c8f37
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854780"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Как выполнить отключение активации по URL-адресу приложений ClickOnce

Как правило, приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запускается автоматически сразу после установки с веб-сервера. По соображениям безопасности можно отключить это поведение и сообщить пользователям, что запускать приложение нужно из меню **Пуск**. Следующая процедура описывает процесс отключения активации через URL.

Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установленных на компьютере пользователя с веб-сервера. Этот метод нельзя использовать для приложений, предназначенных только для использования в Интернете, запустить которые можно только с помощью URL. Дополнительные сведения о различиях между приложениями для использования только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Эта процедура использует Windows Software Development Kit (SDK) средства MageUI.exe. Дополнительные сведения об этом инструменте см. в разделе [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Вы также можете выполнить эту процедуру с помощью Visual Studio.

## <a name="procedure"></a>Процедура

### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL

1.  Откройте манифест развертывания в MageUI.exe. Если еще не создана, выполните действия, описанные в [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2.  Перейдите на вкладку **Параметры развертывания**.

3.  Снимите флажок **Автоматически запускать приложение после установки**.

4.  Сохраните и подпишите манифест.

## <a name="see-also"></a>См. также

- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)