---
title: "Как: проверка обновлений для приложения программным путем с помощью API развертывания ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 02e6a4c0b69bf9e9d6170175b4324ccb226854e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью функций API развертывания технологии ClickOnce
ClickOnce предоставляет два способа обновления приложения после его развертывания. Во-первых можно настроить развертывание технологии ClickOnce для автоматической проверки обновлений через определенные промежутки времени. Во-вторых, можно написать код, использующий <xref:System.Deployment.Application.ApplicationDeployment> класса, чтобы проверить наличие обновлений на основе события, такого как запрос пользователя.  
  
 В следующей процедуре показан код для выполнения программного обновления, а также описывается настройка развертывания ClickOnce для обеспечения проверок программных обновлений.  
  
 Чтобы обновить приложение ClickOnce программно, необходимо указать местоположения для обновлений. Это иногда называется поставщика развертывания. Дополнительные сведения о задании этого свойства см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Также можно использовать метод, описанный ниже, для развертывания приложения из одного места и обновления его из другого. Дополнительные сведения см. в разделе [как: задание альтернативного местоположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Чтобы проверить наличие обновлений программным способом  
  
1.  Создайте новое приложение Windows Forms с помощью средств командной строки или визуальном элементе предпочтительным.  
  
2.  Создайте любые кнопки, меню или другой элемент пользовательского интерфейса требуется пользователям выбирать для проверки наличия обновлений. Из этого элемента в обработчик событий вызовите следующий метод для проверки и установки обновлений.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Скомпилируйте приложение.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Развертывание приложения, которое проверяет наличие обновлений программным способом с помощью Mage.exe  
  
-   Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в статье [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). При вызове Mage.exe для создания манифеста развертывания, убедитесь, что с помощью параметра `providerUrl`, а также указать URL-адрес, где приложение ClickOnce должно проверять наличие обновлений. Если ваше приложение будет обновлять из [http://www.adatum.com/MyApp](http://www.adatum.com/MyApp), например, при вызове создания манифеста развертывания может выглядеть следующим образом:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>С помощью MageUI.exe для развертывания приложения, которое проверяет наличие обновлений программным способом  
  
-   Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в статье [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). На **варианты развертывания** установите **начальное местоположение** поля в манифест приложения ClickOnce должно проверять наличие обновлений. На **параметры обновления** снимите **это приложение должно проверять наличие обновлений** флажок.  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Приложение должно иметь разрешения полного доверия для использования программного обновления.  
  
## <a name="see-also"></a>См. также  
 [Как: задание альтернативного местоположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)