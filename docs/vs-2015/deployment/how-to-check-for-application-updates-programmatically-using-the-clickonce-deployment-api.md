---
title: Инструкции. Проверка обновлений приложения программным путем с помощью API развертывания ClickOnce | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444987"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью функций API развертывания технологии ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Технология ClickOnce предоставляет два способа обновления приложения после его развертывания. В первом методе можно настроить развертывание ClickOnce для автоматической проверки обновлений через определенные промежутки времени. Во втором методе можно написать код, использующий <xref:System.Deployment.Application.ApplicationDeployment> класс для проверки наличия обновлений на основе события, например запроса пользователя.  
  
 В следующих процедурах показан код для выполнения программного обновления, а также описывается настройка развертывания ClickOnce для включения программных проверок обновлений.  
  
 Чтобы обновить приложение ClickOnce программным способом, необходимо указать расположение для обновлений. Иногда это называется поставщиком развертывания. Дополнительные сведения об установке этого свойства см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
> Вы также можете использовать описанный ниже метод, чтобы развернуть приложение из одного расположения, но обновить его с другого. Дополнительные сведения см. [в разделе инструкции. Указание альтернативного расположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Программная проверка обновлений  
  
1. Создайте новое приложение Windows Forms с помощью предпочтительной командной строки или визуальных средств.  
  
2. Создайте любую кнопку, пункт меню или другой элемент пользовательского интерфейса, который пользователи должны выбрать для проверки наличия обновлений. В обработчике событий этого элемента вызовите следующий метод, чтобы проверить наличие обновлений и установить их.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Скомпилируйте приложение.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование Mage.exe для развертывания приложения, которое программно проверяет на наличие обновлений  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). При вызове Mage.exe для создания манифеста развертывания обязательно используйте параметр командной строки `providerUrl` и укажите URL-адрес, по которому ClickOnce должен проверять наличие обновлений. Если приложение будет обновляться с `http://www.adatum.com/MyApp` , например, вызов для создания манифеста развертывания может выглядеть следующим образом:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование MageUI.exe для развертывания приложения, которое программно проверяет на наличие обновлений  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). На вкладке **Параметры развертывания** задайте для поля **начальное расположение** значение манифест приложения ClickOnce, которое должно проверять наличие обновлений. На вкладке **Параметры обновления** снимите флажок **это приложение должно проверять наличие обновлений** .  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Приложение должно иметь разрешения полного доверия для использования программного обновления.  
  
## <a name="see-also"></a>См. также:  
 [Как указать альтернативное расположение для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
