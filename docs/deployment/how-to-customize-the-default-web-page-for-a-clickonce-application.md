---
title: "Как: Настройка веб-страницы по умолчанию для приложения ClickOnce | Документы Microsoft"
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
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 4927a5909ba4b09e796d52d81cc9821a5a9c4820
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Практическое руководство. Настройка используемой по умолчанию веб-страницы для ClickOnce-приложения
При публикации приложения ClickOnce на веб-узле, на веб-странице автоматически создается и публикуется вместе с приложением. По умолчанию страница содержит имя приложения и ссылки для установки приложения, установите необходимые компоненты или справку в библиотеке MSDN.  
  
> [!NOTE]
>  Действительные ссылки, которые вы видите на странице зависят от компьютера, где просмотре страницы и что необходимые компоненты установлены.  
  
 Является именем по умолчанию для веб-страница Publish.htm; можно изменить имя в **конструктора проектов**. Дополнительные сведения см. в разделе [как: укажите публикация страницы для ClickOnce-приложения](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Веб-страница Publish.htm публикуется только в том случае, если обнаружено более новой версии.  
  
> [!NOTE]
>  Изменения, внесенные в вашей **публикации** параметры не влияют на странице Publish.htm, за одним исключением: Если добавить или удалить после первоначальной публикации необходимых компонентов, список необходимых компонентов не будет точным. Необходимо будет изменить текст ссылки на необходимые компоненты для отражения изменений.  
  
### <a name="to-customize-the-publish-web-page"></a>Чтобы настроить веб-страница публикации  
  
1.  Публикация приложения ClickOnce на расположение в Интернете. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с использованием мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  На веб-сервере откройте файл Publish.htm в Visual Web Designer или другой редактор HTML.  
  
3.  Настройка страницы желаемым образом и сохраните его.  
  
4.  Необязательный. Для предотвращения перезаписи опубликовать настроенный веб-страницы в Visual Studio, снимите флажок **автоматически создавать веб-страницу развертывания после каждой публикации** в диалоговом окне Параметры публикации.  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Практическое руководство. Задание страницы публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)