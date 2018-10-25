---
title: Устранение неполадок с безопасностью решений Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 002759a1a5fd8a16ee3e7842df7439d6e6b9755f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862935"
---
# <a name="troubleshoot-office-solution-security"></a>Устранение неполадок с безопасностью решений Office
  В этом разделе содержатся советы по решению типичных проблем, которые могут возникнуть при работе с обеспечение безопасности решений Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Невозможно установить надежными решениями с помощью ограниченных узлов  
 Пользователи не могут устанавливать это решение из Интернета, если веб-узел в зону ограниченных узлов браузера Internet Explorer. Это справедливо, даже если решение подписано доверенным сертификатом.  
  
 URL-адрес манифеста развертывания можно отнести к одному из пяти зон:  
  
- Мой компьютер  
  
- Интернет  
  
- Местная интрасеть  
  
- Надежных сайтов  
  
- Ограниченных узлов  
  
  Если в зону ограниченных узлов, явно назначенной расположение манифеста развертывания [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не устанавливает решение. Если расположение известен и может быть доверенной, пользователь может удалить расположение из зоны ограниченных узлов и установить решение. Сведения о том, как управлять зонами, см. в разделе [Настройка надежных издателей ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Решения невозможно установить с помощью общих сетевых папок или веб-узлов. Если установлена конфигурация усиленной безопасности Internet Explorer или Internet Explorer 7  
 Internet Explorer усиленной безопасности конфигурации (IEESC) в Windows Server 2003 и более поздних версий и Internet Explorer 7 и более поздних версий, значительно ограничивает возможности пользователей в Интернете. При попытке установки решений Office из сетевой общей папки или веб-папки, может возникнуть следующее сообщение об ошибке: «функциональные возможности настроенная в этом приложении не будет работать, поскольку сертификат используется для подписи манифеста развертывания для *SolutionName* не является доверенным. Обратитесь к администратору за дополнительной помощью.»  
  
 В IEESC и Internet Explorer 7 и более поздней версии Если URL-адрес манифеста развертывания относится к категории в зоне Интернета, манифест должен иметь сертификат от доверенного издателя или не удается установить решение. Без IEESC поведение по умолчанию — предлагать пользователю принять решение о доверии.  
  
 Для управления последствия IEESC и Internet Explorer 7 и более поздних версиях определения веб-сайтов и упоминания пути (UNC) соглашения об универсальных доверия и добавить их к одной из зон безопасности ("Местная интрасеть" или "Надежные узлы"). Сведения о том, как управлять зонами, см. в разделе [ClickOnce Настройка доверенных издателей](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>См. также  
 [Безопасные решения Office](../vsto/securing-office-solutions.md)  
  
  