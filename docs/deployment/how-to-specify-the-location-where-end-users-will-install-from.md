---
title: 'Как: укажите расположение, где пользователи будут устанавливать с | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 3161cfb36c09f78911a762347f9c9ec6d125ee39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, место которого пользователи могут загрузить и установить приложение не обязательно является местом, где первоначально было опубликовано приложение. Например в некоторых организациях разработчик может опубликовать приложение на промежуточный сервер и затем администратор перемещает приложение на веб-сервере.  
  
 В этом случае можно использовать `Installation URL` свойство, чтобы указать веб-сервер, который пользователи будут переходить для загрузки приложения. Это необходимо, чтобы манифест приложения знал, где искать обновления.  
  
 `Installation URL` Может быть установлено на **публикации** страница **конструктора проектов**.  
  
 **Примечание** `Installation URL` свойства можно также задать с помощью **PublishWizard**. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с использованием мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Чтобы указать URL-адреса установки  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В поле URL-адрес установки укажите место установки, используя полный URL-адрес в формате http://www.microsoft.com/ApplicationName, или UNC-путь в формате \\\Server\ApplicationName.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Указание расположения, в которое средой Visual Studio копируются файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)