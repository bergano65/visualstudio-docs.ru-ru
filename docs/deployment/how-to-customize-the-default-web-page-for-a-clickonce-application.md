---
title: Настройка веб-страницы по умолчанию для приложения ClickOnce
description: Сведения о веб-странице, созданной при публикации приложения ClickOnce в Интернете, которое содержит имя приложения и другие сведения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900785"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Практическое руководство. Настройка используемой по умолчанию веб-страницы для приложения ClickOnce
При публикации приложения ClickOnce в Интернете автоматически создается и публикуется веб-страница вместе с приложением. Страница по умолчанию содержит имя приложения и ссылки для установки приложения, установки необходимых компонентов или доступа к справке на сайте MSDN.

> [!NOTE]
> Фактические ссылки, отображаемые на странице, зависят от компьютера, на котором просматривается страница, и необходимых компонентов.

 Имя по умолчанию для веб-страницы — *Publish.htm*. имя можно изменить в **конструкторе проектов**. Дополнительные сведения см. [в разделе руководство. Указание страницы публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Веб-страница *Publish.htm* публикуется только при обнаружении более новой версии.

> [!NOTE]
> Изменения, внесенные в параметры **публикации** , не повлияют на *Publish.htm* странице, за одним исключением: Если после первоначальной публикации добавляются или удаляются необходимые компоненты, список необходимых компонентов перестанет быть точным. Необходимо изменить текст ссылки на необходимые компоненты, чтобы отразить изменения.

### <a name="to-customize-the-publish-web-page"></a>Настройка веб-страницы публикации

1. Опубликуйте приложение ClickOnce в веб-расположении. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. На веб-сервере откройте файл *Publish.htm* в Visual Web Designer или другом HTML-редакторе.

3. Настройте страницу по желанию и сохраните ее.

4. Необязательный элемент. Чтобы запретить Visual Studio перезапись настроенной веб-страницы публикации, снимите флажок **автоматически создавать веб-страницу развертывания после каждой публикации** в диалоговом окне **Параметры публикации** .

## <a name="see-also"></a>См. также раздел
- [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Как установить необходимые компоненты с помощью приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Как указать страницу публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)