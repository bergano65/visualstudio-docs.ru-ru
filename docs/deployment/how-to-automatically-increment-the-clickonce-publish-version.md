---
title: Автоматическое увеличение версии публикации ClickOnce
description: Узнайте, как отключить автоматическое увеличение номера редакции для приложения ClickOnce с помощью Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947779"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Практическое руководство. Автоматическое увеличение номера версии публикации ClickOnce

При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения изменение `Publish Version` свойства приводит к публикации приложения в качестве обновления. По умолчанию Visual Studio автоматически увеличивает `Revision` число `Publish Version` раз при публикации приложения.

Это поведение можно отключить на странице **Публикация** в **конструкторе проектов**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Отключение автоматического увеличения версии публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В разделе **Публикация версии** снимите флажок **автоматически увеличивать номер редакции при каждом выпуске** .

## <a name="see-also"></a>См. также раздел

- [Как задать версию публикации ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)