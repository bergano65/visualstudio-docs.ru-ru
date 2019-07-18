---
title: Укажите место для копирования файлов | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec54a2d3150b0e8e11b19d2ca739324d7388f1f0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407652"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Практическое руководство. Указание расположения, в которое средой Visual Studio копируются файлы
При публикации приложения с помощью ClickOnce свойство `Publish Location` указывает расположение, в которое помещены файлы и манифест приложения. Это может быть путь к файлу или путь к FTP-серверу.

 Свойство `Publish Location` можно указать на странице **Публикация** **Конструктора проектов** или с помощью Мастера публикации. Дополнительные сведения см. в разделе [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Если вы устанавливаете больше одной версии приложения с использованием технологии ClickOnce, то более ранние версии приложения перемещаются в папку "Archive", созданную в указанном вами расположении публикации. Архивация более ранних версий предотвращает появление папок с ранними версиями в каталоге установки.

### <a name="to-specify-a-publishing-location"></a>Указание расположения публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле **Расположение публикации** введите расположение публикации, используя один из следующих форматов:

   - Чтобы опубликовать в общую папку или на диск, введите путь, используя UNC-путь (*\\\Server\имя_приложения*) или путь к файлу (*C:\Deploy\имя_приложения*).

   - Для публикации на FTP-сервер введите путь, используя формат <em>ftp://ftp.microsoft.com/\<имя_приложения></em>.

     Обратите внимание, что для работы кнопки обзора (**...**) в поле **Расположение публикации** должен присутствовать текст.

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)