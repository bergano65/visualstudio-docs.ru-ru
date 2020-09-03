---
title: Как указать страницу публикации для приложения ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202158"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Практическое руководство. Задание страницы публикации для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения создается и публикуется веб-страница по умолчанию (publish.htm) вместе с приложением. На этой странице содержится имя приложения, ссылка для установки приложения и (или) необходимых компонентов, а также ссылка на раздел справки, описывающий [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Свойство **страницы Публикация** для проекта позволяет указать имя для веб-страницы [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
 После того как страница публикации указана, при следующей публикации она будет скопирована в расположение публикации. При повторной публикации она не будет перезаписана. Если вы хотите настроить внешний вид страницы, это можно сделать, не беспокоясь о потере изменений. Дополнительные сведения см. в разделе [как настроить веб-страницу ClickOnce по умолчанию](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Свойство **Публикация страницы** можно задать в диалоговом окне **Параметры публикации** , доступном в области **Публикация** **конструктора проектов**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Указание настраиваемой веб-страницы для приложения ClickOnce  
  
1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.  
  
2. Выберите панель **Публикация** .  
  
3. Нажмите кнопку " **Параметры** ", чтобы открыть диалоговое окно " **Параметры публикации** ".  
  
4. Щелкните **Развертывание**.  
  
5. Убедитесь, что в диалоговом окне **Параметры публикации** установлен флажок **Открыть веб-страницу развертывания после публикации** (он должен быть установлен по умолчанию).  
  
6. В поле **веб-страница развертывания:** введите имя веб-страницы и нажмите кнопку **ОК**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Запрет запуска страницы публикации при каждой публикации  
  
1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.  
  
2. Выберите панель **Публикация** .  
  
3. Нажмите кнопку " **Параметры** ", чтобы открыть диалоговое окно " **Параметры публикации** ".  
  
4. Щелкните **Развертывание**.  
  
5. В диалоговом окне **Параметры публикации** снимите флажок **Открыть веб-страницу развертывания после публикации** .  
  
## <a name="see-also"></a>См. также:  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Как настроить веб-страницу ClickOnce по умолчанию](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
