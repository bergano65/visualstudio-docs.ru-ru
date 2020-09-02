---
title: Настройка веб-страницы по умолчанию для приложения ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee4c1211840f17afe371961dea644372cd63efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382475"
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

## <a name="see-also"></a>См. также
- [Безопасность и развертывание ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Как установить необходимые компоненты с помощью приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Практическое руководство. Указание страницы публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)