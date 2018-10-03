---
title: 'Практическое: Укажите, где Visual Studio копирует файлы | Документация Майкрософт'
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
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 52f19317bbfad963dd5bc4dc3e540640f9234c12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570800"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Практическое руководство. Указание расположения, в которое копируются файлы средой Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Укажите, где Visual Studio копирует файлы](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-where-visual-studio-copies-the-files).  
  
При публикации приложения с помощью ClickOnce свойство `Publish Location` указывает расположение, в которое помещены файлы и манифест приложения. Это может быть путь к файлу или путь к FTP-серверу.  
  
 Можно указать `Publish Location` свойство **публикации** странице **конструктор проектов**, или с помощью мастера публикации. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Если вы устанавливаете больше одной версии приложения с использованием технологии ClickOnce, то более ранние версии приложения перемещаются в папку "Archive", созданную в указанном вами расположении публикации. Архивация более ранних версий предотвращает появление папок с ранними версиями в каталоге установки.  
  
### <a name="to-specify-a-publishing-location"></a>Указание расположения публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **расположение публикации** введите расположение публикации с помощью одного из следующих форматов:  
  
    -   Чтобы опубликовать в общую папку или диск путь к файлу, введите путь, используя UNC-путь (\\\Server\ApplicationName) или путь к файлу (C:\Deploy\ApplicationName).  
  
    -   Для публикации на FTP-сервер введите путь, используя формат ftp://ftp.microsoft.com/ApplicationName.  
  
     Обратите внимание на то, что должен присутствовать текст в **расположение публикации** поле для просмотра (**...** ) для работы кнопки.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



