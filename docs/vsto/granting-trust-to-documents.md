---
title: "Присвоение уровня доверия документам | Документы Microsoft"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 31fd8ba79218c6844e8fc5af33a81ce1c95a8abf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="granting-trust-to-documents"></a>Granting Trust to Documents
  К проекту уровня документа предъявляются те же требования безопасности, что и к проектам уровня приложения. Это подписание манифестов сертификатом или подтверждение при запросе доверия. Кроме того, документ или книга должны быть расположены в каталоге, назначенном в качестве надежного расположения.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Надежные расположения  
 Приложения в [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и Office 2010 имеют центры управления безопасностью, в которых пользователи могут настраивать параметры безопасности и конфиденциальности, например надежных расположений. Для решений Office локальный компьютер считается надежным расположением. Однако из-за повышенного риска некоторые каталоги нельзя считать надежными. Это, например, временные системные папки для каждого пользователя и для браузера Internet Explorer.  
  
 Дополнительные сведения о центре управления безопасностью см. в разделе [безопасности политики и параметры в Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Дополнительные сведения о том, как создание, управление, удаление и настройка надежных папок см. в разделе [Настройка надежных расположений и доверенных издателей параметров в выпуске 2007 системы Office](http://go.microsoft.com/fwlink/?LinkId=89203) и [создание, удаление или изменение Надежные расположения для файлов](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Рекомендации по обеспечению безопасности для решений Office  
 При выборе папок для добавления в список надежных расположений необходимо учесть несколько аспектов безопасности.  
  
-   Локальные папки являются более защищенными, поэтому они автоматически считаются надежными. Удаленные местоположения, такие как общие файловые ресурсы, необходимо назначить в качестве надежных расположений.  
  
-   При добавлении каталога в список надежных расположений полное доверие предоставляется не только решениям Office, но также коду VBA и ActiveX. По этой причине корневой каталог и папки «Мои документы» не должны назначаться в качестве доверенных.  
  
-   Хотя сам документ является надежным при использовании надежного расположения, для предоставления доверия в целях настройки необходимы дополнительные разрешения. Вы можете предоставить полное доверие в целях настройки, используя подписание манифестов сертификатом, подтверждая доверие по запросу или установив решение Office в каталог Program Files.  
  
-   Документ или книгу решения на уровне документа можно сохранять в том же каталоге, что и сборку, или в другом каталоге. Например, документ может быть размещен на сервере SharePoint, а сборка может находиться на общем сетевом ресурсе. Дополнительные сведения см. в разделе [как: публикация решения Office уровня документа на сервере SharePoint с помощью ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>См. также  
 [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Устранение неполадок безопасности решений Office](../vsto/troubleshooting-office-solution-security.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  