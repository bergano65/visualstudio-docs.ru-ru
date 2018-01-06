---
title: "Как: задание страницы публикации для приложения ClickOnce | Документы Microsoft"
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 491ef29c955c5ab06b8539ec5089f2ed32feaf36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Практическое руководство. Задание страницы публикации для приложения ClickOnce
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений, веб-страница по умолчанию (publish.htm) создается и публикуется вместе с приложением. Эта страница содержит имя приложения, ссылку для установки приложения и/или необходимых компонентов и ссылку на раздел справки с описанием [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Страницы публикации** свойство проекта можно указать имя для веб-страницы для вашего [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
 После публикации страницы, при очередном публикации, он будет копироваться в место публикации; он не будет переписываться при повторной публикации. Если вы хотите настроить внешний вид страницы, это можно сделать, не беспокоясь о потере изменений. Дополнительные сведения см. в разделе [как: Настройка ClickOnce по умолчанию веб-страницы](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Страницы публикации** может быть установлено **параметры публикации** окне доступен из **публикации** области **конструктора проектов**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Чтобы указать пользовательский веб-страницы для ClickOnce-приложения  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Выберите **публикации** области.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  В **параметры публикации** диалогового окна поле, убедитесь, что **открыть web страницу развертывания после публикации** флажок (он должен быть выбран по умолчанию).  
  
6.  В **веб-страницу развертывания:** введите имя веб-страницы и нажмите кнопку **ОК**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Чтобы предотвратить запуск каждый раз, когда публикации страница публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Выберите **публикации** области.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  В **параметры публикации** снимите флажок **открыть web страницу развертывания после публикации** флажок.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Как: Настройка веб-страницы по умолчанию ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)