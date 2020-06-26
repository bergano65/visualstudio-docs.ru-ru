---
title: Укажите, куда копировать файлы | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0618a6e0b74c16efaaf8a70b7b8745e0f3dd142
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381721"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Практическое руководство. Указание расположения, в которое среда Visual Studio копирует файлы
При публикации приложения с помощью ClickOnce свойство `Publish Location` указывает расположение, в которое помещены файлы и манифест приложения. Это может быть путь к файлу или путь к FTP-серверу.

 Свойство `Publish Location` можно указать на странице **Публикация****Конструктора проектов** или с помощью Мастера публикации. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Если вы устанавливаете больше одной версии приложения с использованием технологии ClickOnce, то более ранние версии приложения перемещаются в папку "Archive", созданную в указанном вами расположении публикации. Архивация более ранних версий предотвращает появление папок с ранними версиями в каталоге установки.

### <a name="to-specify-a-publishing-location"></a>Указание расположения публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле **Расположение публикации** введите расположение публикации, используя один из следующих форматов:

   - Чтобы опубликовать файловый ресурс или путь к диску, введите путь в формате UNC (* \\ \сервер\аппликатионнаме*) или пути к файлу (*к:\деплой\аппликатионнаме*).

   - Для публикации на FTP-сервере введите путь в формате <em>FTP://FTP.Microsoft.com/ \<ApplicationName> </em>.

     Обратите внимание, что в поле **Расположение публикации** должен присутствовать текст, чтобы кнопка обзора (**...**) работала.

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)