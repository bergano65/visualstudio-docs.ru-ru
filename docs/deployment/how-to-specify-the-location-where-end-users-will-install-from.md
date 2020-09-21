---
title: Укажите расположение для установки конечных пользователей
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ba02b1cf8947fa2d1907d6316e36af8f8f54a77
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808728"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями

При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения расположение, в которое пользователи переходят по загрузке и установке, не обязательно является расположением, где первоначально публикуются приложение. Например, в некоторых организациях разработчик может опубликовать приложение на промежуточном сервере, а затем администратор переместит приложение на веб-сервер.

В этом случае можно использовать `Installation URL` свойство, чтобы указать веб-сервер, на который пользователи будут загружать приложение. Это необходимо, чтобы манифест приложения знал, где искать обновления.

Это `Installation URL` свойство можно задать на странице **Публикация** **конструктора проектов**.

> [!NOTE]
> `Installation URL`Свойство также может быть задано с помощью **публикаций**. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Указание URL-адреса установки

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле URL-адрес установки введите путь установки с помощью полного URL-адреса в формате `https://www.contoso.com/ApplicationName` или UNC, используя формат `\Server\ApplicationName` .

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Указание расположения, в которое среда Visual Studio копирует файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)