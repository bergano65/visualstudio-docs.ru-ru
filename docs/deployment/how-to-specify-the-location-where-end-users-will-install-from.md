---
title: Как указать расположение, из которого будут устанавливаться конечные пользователи. Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 993c654ccd16f2d51d86a46a716edd611ae154dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557610"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения расположение, куда пользователи переходят для загрузки и установки приложения, не обязательно является расположением, где первоначально публикуются приложение. Например, в некоторых организациях разработчик может опубликовать приложение на промежуточном сервере, а затем администратор переместит приложение на веб-сервер.

В этом случае можно использовать свойство `Installation URL`, чтобы указать веб-сервер, на который пользователи будут загружать приложение. Это необходимо, чтобы манифест приложения знал, где искать обновления.

Свойство `Installation URL` можно задать на странице **Публикация** **конструктора проектов**.

> [!NOTE]
> Свойство `Installation URL` также может быть задано с помощью **публикаций**. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Указание URL-адреса установки

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле URL-адрес установки введите расположение установки, используя полный URL-адрес в формате `https://www.contoso.com/ApplicationName`или UNC-путь в формате `\Server\ApplicationName`.

## <a name="see-also"></a>См. также:
- [Практическое руководство. Указание расположения, в которое среда Visual Studio копирует файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)