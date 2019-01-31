---
title: Как выполнить Настройка веб-страницы по умолчанию для ClickOnce-приложения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324066d1f6bd6ad1719b2dc960de2b2357ec8cbd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976385"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Как выполнить Настройка используемой по умолчанию веб-страницы для приложения ClickOnce
При публикации приложения ClickOnce на веб-узле, веб-странице автоматически создается и публикуется вместе с приложением. Страница по умолчанию содержит имя приложения и ссылки для установки приложения, установите необходимые компоненты или справку на сайте MSDN.  
  
> [!NOTE]
>  Действительные ссылки, которые отображаются на странице зависят от компьютера, где просмотре страницы и что необходимые компоненты установлены.  
  
 Имя по умолчанию для веб-страницы — *Publish.htm*; можно изменить имя в **конструктор проектов**. Дополнительные сведения см. в разделе [Как задать страницу публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 *Publish.htm* веб-страницы публикуется только в том случае, если обнаружено более новой версии.  
  
> [!NOTE]
>  Изменения, внесенные вашей **публикации** настройки не повлияют *Publish.htm* страницы, за одним исключением: Если добавить или удалить необходимые компоненты после первоначальной публикации, будет список необходимых компонентов больше не будет точным. Необходимо будет изменить текст ссылки на необходимые компоненты для отражения изменений.  
  
### <a name="to-customize-the-publish-web-page"></a>Для настройки веб-страница публикации  
  
1.  Публикация приложения ClickOnce на расположение в Интернете. Дополнительные сведения см. в разделе [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  На веб-сервере, откройте *Publish.htm* файл в Visual Web Designer или другого редактора HTML.  
  
3.  Настройка страницы при необходимости и сохраните его.  
  
4.  Необязательный параметр. Для предотвращения перезаписи настроенной веб страницы публикации Visual Studio, снимите флажок **автоматически создавать веб-страницу развертывания после каждой публикации** в **параметры публикации** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Практическое руководство. Задание страницы публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)