---
title: "Устранение неполадок безопасности решений Office | Документы Microsoft"
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
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3cc5656877f3e6c1ee578a53345e2482c2103223
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-office-solution-security"></a>Устранение неполадок, связанных с безопасностью решений Office
  В этом разделе содержатся советы по решению типичных проблем, которые могут возникнуть при работе с обеспечение безопасности решений Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Надежные решения не может устанавливаться из сайтов с ограниченным доступом  
 Пользователи не могут устанавливать решение из Интернета, если в списке веб-сайт в зону ограниченных узлов браузера Internet Explorer. Это верно, даже если решение подписано с помощью доверенного сертификата.  
  
 URL-адрес манифеста развертывания можно разделить один из пяти зон:  
  
-   Мой компьютер  
  
-   Интернет  
  
-   Местная интрасеть  
  
-   Надежных узлов  
  
-   Ограниченные узлы  
  
 Если расположение манифеста развертывания для зоны ограниченных узлов назначено [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] решение не устанавливается. Если расположение известно и может быть доверенным, пользователь может удалить расположение из зоны ограниченных узлов и установить решение. Сведения об управлении зонами см. в разделе [Настройка надежных издателей ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Решения нельзя установить из общих сетевых папок или веб-сайтах, если конфигурация усиленной безопасности Internet Explorer или установлен Internet Explorer 7  
 Internet Explorer усиленной безопасности конфигурации (IEESC) в Windows Server 2003 или более поздней версии и Internet Explorer 7 и более поздних версий, значительно ограничивает возможности пользователей в Интернете. При попытке установки решений Office из сетевой общей папки или веб-папки, может возникнуть следующее сообщение об ошибке: «настраиваемые функциональные возможности в этом приложении не будут работать, поскольку сертификат используется для подписания манифеста развертывания для *Имя_решения* не является доверенным. Обратитесь к администратору за помощью.»  
  
 В IEESC и Internet Explorer 7 и более поздних версий Если URL-адрес манифеста развертывания к категории в зоне Интернета, манифест должен иметь сертификат от доверенного издателя или не удается установить решение. Без IEESC поведение по умолчанию не предлагается пользователю принять решение о доверии.  
  
 Для управления эффект IEESC и Internet Explorer 7 и более поздних версиях определения веб-сайтов и универсальным именования путей соглашение (UNC), доверия и добавить их в одну из зон безопасности ("Местная интрасеть" или "Надежные узлы"). Сведения об управлении зонами см. в разделе [Настройка надежных издателей ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  