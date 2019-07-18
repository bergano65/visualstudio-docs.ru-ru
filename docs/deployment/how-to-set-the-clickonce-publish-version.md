---
title: Практическое руководство. Установка ClickOnce версии публикации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2bd526203b777bafd77c79a4934d1f3e8754dee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406842"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Практическое руководство. установку версии публикации приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Свойство определяет ли приложение, которое вы публикуете будет рассматриваться как обновление. Каждая версия времени увеличивается, приложение будет опубликовано как обновление.

 `Publish Version` Может быть установлено на **публикации** странице **конструктор проектов**.

> [!NOTE]
> Имеется параметр проекта, который автоматически увеличивает `Publish Version` свойство каждый раз при публикации приложения; этот параметр включен по умолчанию. Дополнительные сведения см. в разделе [Как автоматически увеличить номера версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Изменение версии публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В **версия публикации** поле, приращение **основных**, **незначительные**, **построения**, или **редакции** версии номера.

    > [!NOTE]
    > Вы никогда не следует уменьшения номером версии; Это может привести к непредсказуемым обновления поведение.

## <a name="see-also"></a>См. также
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Практическое руководство. Автоматическое увеличение номера версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)