---
title: Укажите ссылку на службу технической поддержки | Документация Майкрософт
description: Сведения о свойстве URL-адреса поддержки для публикации приложения ClickOnce, которое определяет веб-страницу или общую папку, в которую пользователи получают сведения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Support URL property
- product support, specifying URL for ClickOnce applications
- Web pages, ClickOnce
- Web sites, creating for ClickOnce support
- ClickOnce deployment, specifying support Web page address
- customer support, ClickOnce applications
- URLs, ClickOnce applications
ms.assetid: 500aebee-545e-4831-a78b-b8671a008015
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c0f0a1c6bda564367497306a572f7e9f4012031
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349767"
---
# <a name="how-to-specify-a-link-for-technical-support"></a>Практическое руководство. Указание ссылки на страницу технической поддержки
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения свойство **URL-адреса поддержки** определяет веб-страницу или общую папку, в которую пользователи могут получить сведения о приложении. Это свойство является необязательным; Если этот параметр указан, URL-адрес будет отображаться в диалоговом окне запись приложения **Установка или удаление программ** .

 Свойство **URL-адреса поддержки** можно задать на странице **Публикация** в **конструкторе проектов**.

### <a name="to-specify-a-support-url"></a>Указание URL-адреса поддержки

1. Выберите проект в **обозревателе решений** , а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. Нажмите кнопку " **Параметры** ", чтобы открыть диалоговое окно " **Параметры публикации** ".

4. Щелкните **Описание**.

5. В поле **URL-адрес поддержки** введите полный путь к веб-сайту, веб-странице или общей папке в формате UNC.

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)