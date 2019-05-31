---
title: Практическое руководство. Укажите расположение, где конечные пользователи будут устанавливать с | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3139cb337428dfc0c14e5bae47e682ce169bc81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108507"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, расположение, где пользователи могут загрузить и установить приложение не обязательно расположение, где первоначально было опубликовано приложение. Например в некоторых организациях разработчик может опубликовать приложение на промежуточном сервере, и затем администратор перемещает приложение на веб-сервере.  
  
 В этом случае можно использовать `Installation URL` свойство, чтобы указать веб-сервер, где пользователи будут переходить для загрузки приложения. Это необходимо, чтобы манифест приложения знал, где искать обновления.  
  
 `Installation URL` Может быть установлено на **публикации** странице **конструктор проектов**.  
  
 **Примечание** `Installation URL` свойства можно также задать с помощью **мастере публикаций**. Дополнительные сведения см. в разделе [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Чтобы указать URL-адрес установки  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В поле URL-адрес установки, введите расположение установки, используя полный URL-адрес в формате http://www.microsoft.com/ApplicationName, или UNC-путь в формате \\\Server\ApplicationName.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Укажите, где Visual Studio копирует файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
