---
title: 'Практическое: задание альтернативного местоположения для обновлений развертывания | Документация Майкрософт'
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
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a0db7eddc38a2b2ab3581ba2b1ff04c90e2adb77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573265"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Практическое руководство. Задание альтернативного местоположения для обновлений развертывания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: задание альтернативного местоположения для обновлений развертывания](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-an-alternate-location-for-deployment-updates).  
  
Вы можете установить ваш [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application из компакт-диске или в общей папке, а приложение должно проверять наличие периодических обновлений в Интернете. Таким образом, приложение может обновляться из Интернета после начальной установки, можно указать альтернативное расположение для обновлений в манифесте развертывания.  
  
> [!NOTE]
>  Чтобы установить локально для использования этой функции необходимо настроить приложение. Дополнительные сведения см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Кроме того, при установке [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения из сети, настройка альтернативного местоположения причины [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] использует это местоположение для первоначальной установки и все последующие обновления. Если установить приложение локально (например, с компакт-диска), первоначальной установки выполняется с помощью исходного носителя, а все последующие обновления будут использовать альтернативное расположение.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Задание альтернативного местоположения для обновлений с помощью MageUI.exe (служебная программа на базе Windows Forms)  
  
1.  Откройте командную строку .NET Framework и введите:  
  
     **MageUI.exe**  
  
2.  На **файл** меню, выберите **откройте** открыть манифест развертывания для приложения.  
  
3.  Выберите **варианты развертывания** вкладки.  
  
4.  В текстовом поле с именем **место запуска**, введите URL-адрес в каталог, который будет содержать манифест развертывания для обновлений приложения.  
  
5.  Сохраните манифест развертывания.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Задание альтернативного местоположения для обновлений с помощью Mage.exe  
  
1.  Откройте командную строку .NET Framework.  
  
2.  Задайте расположение обновления, используя следующую команду. В этом примере **HelloWorld.exe.application** — это путь к вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифеста приложения, который всегда имеет расширение .application, и **http://adatum.com/Update/Path** является URL-адрес этого [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] будет проверять наличие обновлений приложения.  
  
     **Mage-обновление HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Сохраните файл.  
  
    > [!NOTE]
    >  Теперь вам нужно повторно подписать файла с помощью Mage.exe. Дополнительные сведения см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Если установить приложение с автономного носителя, например компакт-диска, и компьютер находится в сети, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] сначала проверяет URL-адрес, определяемое `<deploymentProvider>` тег в манифесте развертывания, чтобы определить, содержит ли расположение обновлений в более поздней версии приложение. В этом случае [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] устанавливает приложение непосредственно из него, а не из исходного каталога установки, и общеязыковой среды выполнения (CLR) определяет доверия для приложения уровня с помощью `<deploymentProvider>`. Если компьютер находится в автономном режиме, или `<deploymentProvider>` недоступен, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] установки с компакт-диска, а среда CLR предоставляет доверие, на основе точки установки; для установки компакт-диска, это означает, приложение получает полного доверия. Все последующие обновления будут наследовать этот уровень доверия.  
  
 Все [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложений, использующих `<deploymentProvider>` должны явно объявлять права, необходимые в манифесте приложения, таким образом, чтобы приложение получало другие уровни доверия на разных компьютерах.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)



