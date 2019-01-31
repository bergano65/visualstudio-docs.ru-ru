---
title: Как выполнить Автоматически ClickOnce увеличение номера версии публикации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 174506e9ee88de385f5bbba6fe09276d9297f298
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937708"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Как выполнить автоматическое увеличение номера версии публикации ClickOnce

При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, изменив `Publish Version` свойство заставляет приложение публикуется как обновление. По умолчанию Visual Studio автоматически увеличивает `Revision` число `Publish Version` при каждой публикации приложения.

Это поведение можно отключить на **публикации** странице **конструктор проектов**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Автоматическое отключение увеличения номера версии публикации

1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2.  Перейдите на вкладку **Публикация**.

3.  В **версия публикации** снимите **автоматически увеличивать номер редакции при каждой редакции** "флажок".

## <a name="see-also"></a>См. также

- [Практическое руководство. Установка версии публикации приложения ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)