---
title: 'Как: Проверьте наличие обновлений приложений, программно используя API развертывания ClickOnce (ru) Документы Майкрософт'
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
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5250e719cce945bdcce90a9d49d2ed8c27555612
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444987"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью функций API развертывания технологии ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce предоставляет два способа обновления приложения после его развертывания. В первом методе можно настроить развертывание ClickOnce для автоматической проверки обновлений через определенные промежутки времени. Во втором методе можно написать <xref:System.Deployment.Application.ApplicationDeployment> код, который использует класс для проверки обновлений на основе события, например запроса пользователя.  
  
 Следующие процедуры показывают некоторый код для выполнения программного обновления, а также описывают, как настроить развертывание ClickOnce, чтобы включить программные проверки обновления.  
  
 Для того, чтобы обновить приложение ClickOnce программно, необходимо указать местоположение для обновления. Иногда это называется поставщиком развертывания. Для получения дополнительной информации об установке этого свойства, [см.](../deployment/choosing-a-clickonce-update-strategy.md)  
  
> [!NOTE]
> Вы также можете использовать описанный ниже метод для развертывания приложения из одного места, но для обновления его из другого. Для получения дополнительной [информации](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)см.  
  
### <a name="to-check-for-updates-programmatically"></a>Для проверки на программное оформление обновлений  
  
1. Создайте новое приложение Windows Forms с помощью предпочтительных командных или визуальных инструментов.  
  
2. Создавайте любую кнопку, элемент меню или другой элемент пользовательского интерфейса, который вы хотите, чтобы пользователи выбрали для проверки обновлений. Из обработчика событий этого элемента позвоните следующему методу для проверки и установки обновлений.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Составить заявку.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование Mage.exe для развертывания приложения, которое проверяет на наличие обновлений в программном плане  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как это объясняется в [Walkthrough: Ручноразвертывание приложения ClickOnce.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) При вызове Mage.exe для генерации манифеста развертывания убедитесь в использовании коммутатора `providerUrl`командной строки и укажите URL,где ClickOnce должен проверить наличие обновлений. Если приложение будет `http://www.adatum.com/MyApp`обновляться, например, вызов для генерации манифеста развертывания может выглядеть следующим образом:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование MageUI.exe для развертывания приложения, которое проверяет на наличие обновлений за программно  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как это объясняется в [Walkthrough: Ручноразвертывание приложения ClickOnce.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) На вкладке **Параметры развертывания** установите поле **стартового местоположения** в манифестприложения ClickOnce, чтобы проверить наличие обновлений. На вкладке **Параметры обновления,** очистить **Это приложение должно проверить для обновления** флажок.  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Ваше приложение должно иметь полностью доверительные разрешения на использование программного обновления.  
  
## <a name="see-also"></a>См. также:  
 [Как: Указать альтернативное местоположение для обновления развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Публикация ClickOnce-приложений](../deployment/publishing-clickonce-applications.md)
