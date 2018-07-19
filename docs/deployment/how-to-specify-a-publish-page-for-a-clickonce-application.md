---
title: 'Практическое: задание страницы публикации для приложения ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 265c1d777da7703dbaa0dd7146a3142e8b7ddffa
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077985"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Практическое: задание страницы публикации для приложения ClickOnce
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, веб-страницы по умолчанию (publish.htm) создается и публикуется вместе с приложением. Эта страница содержит имя приложения, со ссылкой для установки приложения и/или все необходимые компоненты и ссылку на раздел справки с описанием [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Страницы публикации** свойство проекта можно указать имя для веб-страницы для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
 После указания страница публикации в следующий раз вы публикуете, он будет копироваться в место публикации; он не будут перезаписаны при повторной публикации. Если вы хотите настроить внешний вид страницы, это можно сделать, не беспокоясь о потере изменений. Дополнительные сведения см. в разделе [как: Настройка веб-страницы по умолчанию ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Страницы публикации** может быть установлено **параметры публикации** окне доступен из **публикации** области **конструктор проектов**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Чтобы указать пользовательские веб-страницы для ClickOnce-приложения  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Выберите **публикации** области.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  В **параметры публикации** диалогового окна поле, убедитесь, что **откройте развертывания веб-страницу после публикации** флажок (он должен быть установлен по умолчанию).  
  
6.  В **веб-страницу развертывания** введите имя веб-страницы и нажмите кнопку **ОК**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Чтобы предотвратить запуск каждый раз при публикации странице публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Выберите **публикации** области.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  В **параметры публикации** снимите флажок **откройте развертывания веб-страницу после публикации** "флажок".  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Практическое: Настройка веб-страницы по умолчанию ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)