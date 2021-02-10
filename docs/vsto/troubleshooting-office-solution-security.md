---
title: Устранение неполадок в системе безопасности решений Office
description: Ознакомьтесь с советами по решению распространенных проблем, которые могут возникнуть при работе с безопасностью Microsoft Office решений.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04b68a8207dad1edf83462a8284a69c73c668006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969208"
---
# <a name="troubleshoot-office-solution-security"></a>Устранение неполадок в системе безопасности решений Office
  Этот раздел содержит советы по решению распространенных проблем, которые могут возникнуть при работе с обеспечением безопасности решений Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Доверенные решения нельзя устанавливать с ограниченных сайтов
 Пользователи не могут установить решение из расположения в Интернете, если веб-сайт указан в зоне ограниченных сайтов в Internet Explorer. Это справедливо, даже если решение подписано доверенным сертификатом.

 URL-адрес манифеста развертывания можно разделить на одну из пяти зон:

- Мой компьютер

- Интернет

- Местная интрасеть

- Надежные сайты

- Ограниченные сайты

  Если расположение манифеста развертывания было назначено зоне ограниченных узлов, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не устанавливает решение. Если расположение известно и может быть доверенным, пользователь может удалить расположение из зоны ограниченных узлов и установить решение. Сведения об управлении зонами см. в разделе [Настройка доверенных издателей ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Решения не могут быть установлены из сетевых файловых ресурсов или веб-расположений, когда установлена усиленная конфигурация безопасности Internet Explorer или Internet Explorer 7.
 Конфигурация усиленной безопасности Internet Explorer (ИИСК) в Windows Server 2003 и более поздних версиях, а также Internet Explorer 7 и более поздних версий значительно ограничивают возможность пользователей просматривать Интернет. Когда пользователи пытаются установить решения Office из сетевой общей папки или из расположения в Интернете, они могут получить следующее сообщение об ошибке: "настроенные функциональные возможности в этом приложении не будут работать, так как сертификат, используемый для подписи манифеста развертывания для *имяРешения* , не является доверенным. Обратитесь за помощью к администратору ".

 В ИИСК и Internet Explorer 7 и более поздних версиях, если URL-адрес манифеста развертывания классифицирован в зоне Интернета, манифест должен иметь сертификат от доверенного издателя, или решение не может быть установлено. Без ИИСК поведением по умолчанию является запрос конечного пользователя принять решение о доверии.

 Чтобы управлять действиями ИИСК и Internet Explorer 7 и более поздних версий, вычислить веб-сайты и пути в формате UNC, которые вы доверяете, и добавить их в одну из доверенных зон безопасности (локальная интрасеть или надежные сайты). Сведения об управлении зонами см. в разделе [Configure ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>См. также раздел
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
