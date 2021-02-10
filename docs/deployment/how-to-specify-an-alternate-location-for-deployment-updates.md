---
title: Укажите альтернативное расположение для обновлений развертывания
description: Узнайте, как указать альтернативное расположение обновлений для приложения ClickOnce в манифесте развертывания.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f0832105ccc203dd046461e40d27f8d50efc3009
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940375"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Практическое руководство. Задание альтернативного местоположения для обновлений развертывания
Приложение можно установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] изначально с компакт-диска или из общей папки, но приложение должно проверять наличие периодических обновлений в Интернете. Можно указать альтернативное расположение для обновлений в манифесте развертывания, чтобы приложение можно было обновлять из Интернета после первоначальной установки.

> [!NOTE]
> Приложение должно быть настроено для локальной установки с целью использования этой функции. Дополнительные сведения см. [в разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Кроме того, если установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение из сети, то при настройке альтернативного расположения будет [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использоваться это расположение как для первоначальной установки, так и для всех последующих обновлений. Если приложение устанавливается локально (например, с компакт-диска), начальная установка выполняется с использованием исходного носителя, а все последующие обновления будут использовать альтернативное расположение.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Укажите альтернативное расположение для обновлений с помощью MageUI.exe (служебная программа на основе Windows Forms).

1. Откройте командную строку платформа .NET Framework и введите:

     **mageui.exe**

2. В меню **файл** выберите **Открыть** , чтобы открыть манифест развертывания приложения.

3. Перейдите на вкладку **Параметры развертывания**.

4. В текстовом поле имя **запуска** введите URL-адрес каталога, который будет содержать манифест развертывания для обновлений приложения.

5. Сохраните манифест развертывания.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Укажите альтернативное расположение для обновлений с помощью Mage.exe

1. Откройте командную строку .NET Framework.

2. Задайте расположение обновления с помощью следующей команды. В этом примере *HelloWorld.exe. Application* — это путь к [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесту приложения, который всегда имеет расширение приложения, а `http://adatum.com/Update/Path` — это URL-адрес, который [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет проверять наличие обновлений приложения.

    **Mage: обновление HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**

3. Сохраните файл.

   > [!NOTE]
   > Теперь необходимо повторно подписать файл с помощью *Mage.exe*. Дополнительные сведения см. [в разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Безопасность .NET Framework
 Если приложение устанавливается с автономного носителя, такого как компакт-диск, и компьютер находится в сети, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] сначала проверяет URL-адрес, указанный `<deploymentProvider>` тегом в манифесте развертывания, чтобы определить, содержит ли расположение обновления более новую версию приложения. Если это так, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] устанавливает приложение непосредственно из каталога начальной установки, а среда CLR определяет уровень доверия приложения с помощью `<deploymentProvider>` . Если компьютер находится в автономном режиме или `<deploymentProvider>` недоступен, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] устанавливается с компакт-диска, а среда CLR предоставляет доверие на основе точки установки; для установки с компакт-диска это означает, что приложение получает полное доверие. Все последующие обновления наследуют этот уровень доверия.

 Все [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, использующие, `<deploymentProvider>` должны явно объявлять разрешения, необходимые им в манифесте приложения, чтобы приложение не получало разные уровни доверия на разных компьютерах.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)