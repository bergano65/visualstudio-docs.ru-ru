---
title: 'Практическое: укажите расположение, где конечные пользователи будут устанавливать с | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 68f50fe847d1432292491cd2970c7897eb1388da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570029"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите расположение где конечным пользователям будет установить из](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-location-where-end-users-will-install-from).  
  
При публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, расположение, где пользователи могут загрузить и установить приложение не обязательно расположение, где первоначально было опубликовано приложение. Например в некоторых организациях разработчик может опубликовать приложение на промежуточном сервере, и затем администратор перемещает приложение на веб-сервере.  
  
 В этом случае можно использовать `Installation URL` свойство, чтобы указать веб-сервер, где пользователи будут переходить для загрузки приложения. Это необходимо, чтобы манифест приложения знал, где искать обновления.  
  
 `Installation URL` Может быть установлено на **публикации** странице **конструктор проектов**.  
  
 **Примечание** `Installation URL` свойства можно также задать с помощью **мастере публикаций**. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Чтобы указать URL-адрес установки  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В поле URL-адрес установки, введите расположение установки, используя полный URL-адрес в формате http://www.microsoft.com/ApplicationName, или UNC-путь в формате \\\Server\ApplicationName.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Указание расположения, в которое средой Visual Studio копируются файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



