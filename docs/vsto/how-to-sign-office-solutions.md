---
title: "Как: подписывание решений Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12a367b6051f7ed1ca1f51e0c9d7e8ada4be4ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-sign-office-solutions"></a>Практическое руководство. Подписывание решений Office
  Если вы подписываете решение, можно предоставить доверия решению с помощью сертификата в качестве свидетельства. Тот же сертификат можно использовать для нескольких решений и всех решений будет доверять без обновлений политики обеспечения дополнительной безопасности.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если вы вручную не измените приложения и манифестов развертывания с помощью манифеста средства создания и редактирования (mage.exe и mageui.exe), перед использованием их необходимо повторной подписи манифестов. Для получения дополнительной информации см. [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>С помощью сертификата подписи  
 Сертификат — это файл, содержащий уникальный ключ, идентифицирующий издателя решения. Можно приобретать сертификаты из центра сертификации, или создать собственный сертификат и подписать его сертификации.  
  
 Visual Studio решения Office подписываются с временный сертификат для включения отладки. Временный сертификат не следует использовать в решениях, развернутых в качестве свидетельства.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Для подписи решения Office с помощью сертификата  
  
1.  На **проекта** меню, нажмите кнопку *имя_решения***свойства**.  
  
2.  Откройте вкладку **Подписывание**.  
  
3.  Выберите **подписать манифесты ClickOnce**.  
  
4.  Найдите сертификат, нажав кнопку **выбрать из хранилища** или **выбор из файла** и переход к сертификату.  
  
5.  Чтобы убедиться, что используется правильный сертификат, нажмите кнопку **Подробнее** для просмотра сведений о сертификате.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Страница "Подписывание" в конструкторе проектов](/visualstudio/ide/reference/signing-page-project-designer)  
  
  