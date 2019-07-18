---
title: Практическое руководство. Задание страницы публикации для приложения ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29d83dd1a232ae1cf0437c1ab6d4662acef2900d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928340"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Практическое руководство. Задание страницы публикации для приложения ClickOnce
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, веб-страницы по умолчанию (publish.htm) создается и публикуется вместе с приложением. Эта страница содержит имя приложения, со ссылкой для установки приложения и/или все необходимые компоненты и ссылку на раздел справки с описанием [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Страницы публикации** свойство проекта можно указать имя для веб-страницы для вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

 После указания страница публикации в следующий раз вы публикуете, он будет копироваться в место публикации; он не будут перезаписаны при повторной публикации. Если вы хотите настроить внешний вид страницы, это можно сделать, не беспокоясь о потере изменений. Дополнительные сведения см. в разделе [Как Настройка используемой по умолчанию веб-страницы для ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 **Страницы публикации** может быть установлено **параметры публикации** окне доступен из **публикации** области **конструктор проектов**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Чтобы указать пользовательские веб-страницы для ClickOnce-приложения

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Выберите **публикации** области.

3. Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.

4. Нажмите кнопку **развертывания**.

5. В **параметры публикации** диалогового окна поле, убедитесь, что **откройте развертывания веб-страницу после публикации** флажок (он должен быть установлен по умолчанию).

6. В **веб-страницу развертывания** введите имя веб-страницы и нажмите кнопку **ОК**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Чтобы предотвратить запуск каждый раз при публикации странице публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Выберите **публикации** области.

3. Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.

4. Нажмите кнопку **развертывания**.

5. В **параметры публикации** снимите флажок **откройте развертывания веб-страницу после публикации** "флажок".

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Практическое руководство. Настройка используемой по умолчанию веб-страницы для ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)