---
title: 'Как: подписывание решений Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5fa4a837de66a39502e2c9e2d8466f3998acc4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262195"
---
# <a name="how-to-sign-office-solutions"></a>Как: подписывание решений Office
  Если вы подписываете решение, можно предоставить доверия решению с помощью сертификата в качестве свидетельства. Тот же сертификат можно использовать для нескольких решений и всех решений будет доверять без обновлений политики обеспечения дополнительной безопасности.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если вы вручную не измените приложения и манифестов развертывания с помощью манифеста средства создания и редактирования (*mage.exe* и *mageui.exe*), перед использованием их необходимо повторной подписи манифестов. Дополнительные сведения см. в разделе [как: повторной подписи манифестов приложения и развертывания](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Войдите с помощью сертификата  
 Сертификат — это файл, содержащий уникальный ключ, идентифицирующий издателя решения. Можно приобретать сертификаты из центра сертификации, или создать собственный сертификат и подписать его сертификации.  
  
 Visual Studio решения Office подписываются с временный сертификат для включения отладки. Временный сертификат не следует использовать в решениях, развернутых в качестве свидетельства.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Для подписи решения Office с помощью сертификата  
  
1.  На **проекта** меню, щелкните * имя_решения ***свойства**.  
  
2.  Откройте вкладку **Подписывание**.  
  
3.  Выберите **подписать манифесты ClickOnce**.  
  
4.  Найдите сертификат, нажав кнопку **выбрать из хранилища** или **выбор из файла** и переход к сертификату.  
  
5.  Чтобы убедиться, что используется правильный сертификат, нажмите кнопку **Подробнее** для просмотра сведений о сертификате.  
  
## <a name="see-also"></a>См. также  
 [Безопасные решения Office](../vsto/securing-office-solutions.md)   
 [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Страница "Подписывание" в конструкторе проектов](/visualstudio/ide/reference/signing-page-project-designer)  
  
  