---
title: 'Как: подписывание решений Office | Документы Microsoft'
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
ms.openlocfilehash: 31b5e1fc3c78aecf518af0941a4a2dd0ab7e57c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-sign-office-solutions"></a>Практическое руководство. Подписывание решений Office
  Если вы подписываете решение, можно предоставить доверия решению с помощью сертификата в качестве свидетельства. Тот же сертификат можно использовать для нескольких решений и всех решений будет доверять без обновлений политики обеспечения дополнительной безопасности.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если вы вручную не измените приложения и манифестов развертывания с помощью манифеста средства создания и редактирования (mage.exe и mageui.exe), перед использованием их необходимо повторной подписи манифестов. Для получения дополнительной информации см. [Практическое руководство. Повторное подписание манифестов приложения и развертывания](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>С помощью сертификата подписи  
 Сертификат — это файл, содержащий уникальный ключ, идентифицирующий издателя решения. Можно приобретать сертификаты из центра сертификации, или создать собственный сертификат и подписать его сертификации.  
  
 Visual Studio решения Office подписываются с временный сертификат для включения отладки. Временный сертификат не следует использовать в решениях, развернутых в качестве свидетельства.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Для подписи решения Office с помощью сертификата  
  
1.  На **проекта** меню, щелкните * имя_решения ***свойства**.  
  
2.  Откройте вкладку **Подписывание**.  
  
3.  Выберите **подписать манифесты ClickOnce**.  
  
4.  Найдите сертификат, нажав кнопку **выбрать из хранилища** или **выбор из файла** и переход к сертификату.  
  
5.  Чтобы убедиться, что используется правильный сертификат, нажмите кнопку **Подробнее** для просмотра сведений о сертификате.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Страница "Подписывание" в конструкторе проектов](/visualstudio/ide/reference/signing-page-project-designer)  
  
  