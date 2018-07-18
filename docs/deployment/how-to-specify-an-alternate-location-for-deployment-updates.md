---
title: 'Как: задание альтернативного местоположения для обновлений развертывания | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14c6778d5cad698e6eea541b94df6f8eb793746c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561354"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Практическое руководство. Задание альтернативного местоположения для обновлений развертывания
Можно установить на [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения изначально с компакт-диска или из общей папки, но приложение должно проверять наличие периодических обновлений в Интернете. Можно указать альтернативное расположение для обновлений в манифесте развертывания, чтобы ваше приложение может обновляться из Интернета после начальной установки.  
  
> [!NOTE]
>  Приложение должно быть настроено для установки локально, чтобы использовать эту функцию. Дополнительные сведения см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Кроме того, при установке [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения из сети, настройка альтернативного местоположения причины [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует это местоположение для первоначальной установки и все последующие обновления. При установке приложения локально (например, с компакт-диска), первоначальная установка выполняется с исходного носителя, а все последующие обновления будут использовать альтернативное расположение.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Задание альтернативного местоположения для обновлений с помощью MageUI.exe (служебная программа на основе Windows Forms)  
  
1.  Откройте командную строку .NET Framework и введите:  
  
     **MageUI.exe**  
  
2.  На **файл** меню, выберите **откройте** открыть манифест развертывания для приложения.  
  
3.  Выберите **варианты развертывания** вкладки.  
  
4.  В текстовом поле с именем **место запуска**, введите URL-адрес в каталог, который будет содержать манифест развертывания для обновлений приложения.  
  
5.  Сохраните манифест развертывания.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Задание альтернативного местоположения для обновлений с помощью Mage.exe  
  
1.  Откройте командную строку .NET Framework.  
  
2.  Задайте расположение обновления, используя следующую команду. В этом примере **HelloWorld.exe.application** — это путь к вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения, который всегда имеет расширением .application, и **http://adatum.com/Update/Path** является URL-адрес этого [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет проверять наличие обновлений приложения.  
  
     **Mage-обновление HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Сохраните файл.  
  
    > [!NOTE]
    >  Необходимо заново подписать файл с помощью Mage.exe. Дополнительные сведения см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Если установить приложение с автономного носителя, например компакт-диска, и компьютер находится в сети, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] сначала проверяет URL-адрес указанный `<deploymentProvider>` тег в манифесте развертывания, чтобы определить, содержит ли расположение обновлений в более поздней версии приложение. В этом случае [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] устанавливает приложение непосредственно оттуда, а не из исходного каталога установки, и общеязыковой среды выполнения (CLR) определяет доверия для приложения уровня с помощью `<deploymentProvider>`. Если компьютер находится в автономном режиме или `<deploymentProvider>` недоступен, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установки с компакт-диска и среда CLR предоставляет доверия, основанное на точку установки; для установки компакт-диска, это означает ваше приложение получает полное доверие. Все последующие обновления наследуют этот уровень доверия.  
  
 Все [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений, использующих `<deploymentProvider>` должны явно объявить права, необходимые в манифесте приложения, чтобы приложение не получает различные уровни доверия на разных компьютерах.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)