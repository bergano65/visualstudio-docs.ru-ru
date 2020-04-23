---
title: 'Как: Указать альтернативное местоположение для обновления развертывания (ru) Документы Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037224"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Практическое руководство. Задание альтернативного местоположения для обновлений развертывания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] установить приложение изначально с компакт-диска или файла, но приложение должно проверить периодические обновления в Интернете. Можно указать альтернативное место для обновления в манифесте развертывания, чтобы приложение смогли обновиться из Интернета после его первоначальной установки.  
  
> [!NOTE]
> Приложение должно быть настроено для локальной установки для использования этой функции. Для получения дополнительной информации смотрите [Пошаговое руководство: Ручное развертывание приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Кроме того, если [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] вы установите приложение из сети, установка альтернативного местоположения вызывает [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] использование этого местоположения как для первоначальной установки, так и для всех последующих обновлений. Если вы установите приложение локально (например, с компакт-диска), начальная установка выполняется с помощью исходного носителя, и все последующие обновления будут использовать альтернативное местоположение.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Определение альтернативного местоположения для обновлений с помощью MageUI.exe (утилита на основе Windows Forms)  
  
1. Откройте запрос и тип команды .NET Framework:  
  
     **mageui.exe**  
  
2. В меню **файла** выберите **Open,** чтобы открыть манифест развертывания приложения.  
  
3. Перейдите на вкладку **Параметры развертывания**.  
  
4. В текстовом поле под названием **«Место запуска»** введите URL-адрес в каталог, который будет содержать манифест развертывания для обновлений приложений.  
  
5. Сохранить манифест развертывания.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Определение альтернативного местоположения для обновлений с помощью Mage.exe  
  
1. Откройте командную строку .NET Framework.  
  
2. Установите место обновления с помощью следующей команды. В этом примере **HelloWorld.exe.application** — [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] это путь к манифесту приложения, `http://adatum.com/Update/Path` который всегда [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] имеет расширение .application, и URL- данный URL, который будет проверять обновления приложения.  
  
     **Маг -Обновление HelloWorld.exe.application-ProviderUrl\/http: /adatum.com/Update/Path**  
  
3. Сохраните файл.  
  
    > [!NOTE]
    > Теперь вам нужно повторно подписать файл с Mage.exe. Для получения дополнительной информации смотрите [Пошаговое руководство: Ручное развертывание приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Если вы устанавливаете приложение из автономной среды, такой как [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] компакт-диск, и `<deploymentProvider>` компьютер находится в сети, сначала проверьте URL, указанный тегом в манифесте развертывания, чтобы определить, содержит ли местоположение обновления более позднюю версию приложения. Если это [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] так, устанавливает приложение непосредственно оттуда, а не из первоначального каталога установки, и общее время выполнения `<deploymentProvider>`языка (CLR) определяет уровень доверия вашего приложения с помощью. Если компьютер находится в `<deploymentProvider>` автономном режиме [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] или недосягаем, устанавливается с компакт-диска, и CLR предоставляет доверие в зависимости от точки установки; для установки компакт-диска это означает, что ваше приложение получает полное доверие. Все последующие обновления унаследуют этот уровень доверия.  
  
 Все [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, `<deploymentProvider>` которые используют должны прямо объявить разрешения, необходимые им в их манифесте приложения, так что приложение не получает различных уровней доверия на разных компьютерах.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговая инструкция: Вручную развертывание приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Развертывание Манифест](../deployment/clickonce-deployment-manifest.md)   
 [Обеспечение ClickOnce приложений](../deployment/securing-clickonce-applications.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
