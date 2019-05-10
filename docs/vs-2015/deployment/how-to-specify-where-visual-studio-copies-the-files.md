---
title: Практическое руководство. Укажите, где файлы копии Visual Studio 2015 г. | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226159"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Практическое руководство. Указание расположения, в которое средой Visual Studio копируются файлы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При публикации приложения с помощью ClickOnce свойство `Publish Location` указывает расположение, в которое помещены файлы и манифест приложения. Это может быть путь к файлу или путь к FTP-серверу.

 Свойство `Publish Location` можно указать на странице **Публикация** **Конструктора проектов** или с помощью Мастера публикации. Дополнительные сведения см. в разделе [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Если вы устанавливаете больше одной версии приложения с использованием технологии ClickOnce, то более ранние версии приложения перемещаются в папку "Archive", созданную в указанном вами расположении публикации. Архивация более ранних версий предотвращает появление папок с ранними версиями в каталоге установки.

### <a name="to-specify-a-publishing-location"></a>Указание расположения публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле **Расположение публикации** введите расположение публикации, используя один из следующих форматов:

   - Чтобы опубликовать в общую папку или диск путь к файлу, введите путь, используя UNC-путь (\\\Server\ApplicationName) или путь к файлу (C:\Deploy\ApplicationName).

   - Чтобы опубликовать на FTP-сервер, введите путь, используя формат ftp:\//ftp.microsoft.com/ApplicationName.

     Обратите внимание, что для работы кнопки обзора (**...**) в поле **Расположение публикации** должен присутствовать текст.

## <a name="see-also"></a>См. также
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md) [как: Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
