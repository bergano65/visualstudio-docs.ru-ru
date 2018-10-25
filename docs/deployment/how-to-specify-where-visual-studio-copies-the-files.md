---
title: 'Практическое: Укажите, где Visual Studio копирует файлы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cc4e6b3ad623497f50f60b5eb3c0d7c8b00b1cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869591"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Практическое: Укажите, где Visual Studio копирует файлы
При публикации приложения с помощью ClickOnce свойство `Publish Location` указывает расположение, в которое помещены файлы и манифест приложения. Это может быть путь к файлу или путь к FTP-серверу.  
  
 Можно указать `Publish Location` свойство **публикации** странице **конструктор проектов**, или с помощью мастера публикации. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Если вы устанавливаете больше одной версии приложения с использованием технологии ClickOnce, то более ранние версии приложения перемещаются в папку "Archive", созданную в указанном вами расположении публикации. Архивация более ранних версий предотвращает появление папок с ранними версиями в каталоге установки.  
  
### <a name="to-specify-a-publishing-location"></a>Указание расположения публикации  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Нажмите кнопку **публикации** вкладки.  
  
3. В **расположение публикации** введите расположение публикации с помощью одного из следующих форматов:  
  
   - Чтобы опубликовать в общую папку или диск путь к файлу, введите путь, используя UNC-путь (*\\\Server\ApplicationName*) или путь к файлу (*C:\Deploy\ApplicationName*).  
  
   - Чтобы опубликовать на FTP-сервер, введите путь в формате <em>ftp://ftp.microsoft.com/\<ApplicationName ></em>.  
  
     Обратите внимание на то, что должен присутствовать текст в **расположение публикации** поле для просмотра (**...** ) для работы кнопки.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)