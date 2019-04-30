---
title: Практическое руководство. Изменение языка публикации для приложения ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88114080b8de02b3aaba52b0a48fd09d58ec5818
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406654"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Практическое руководство. Изменение языка публикации для приложения ClickOnce

При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, пользовательский интерфейс во время установки значения по умолчанию для языка и региональных параметров компьютера разработки. Если вы публикуете локализованного приложения, необходимо будет указать язык и региональные параметры, соответствующие локализованной версии. Это определяется параметром `Publish language` свойство проекта.

`Publish language` Может быть установлено **параметры публикации** окне доступен из **публикации** странице **конструктор проектов**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Чтобы изменить язык публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.

4. Нажмите кнопку **описание**.

5. В **параметры публикации** диалоговое окно, выберите язык и язык и региональные параметры из **язык публикации** стрелку раскрывающегося списка и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)