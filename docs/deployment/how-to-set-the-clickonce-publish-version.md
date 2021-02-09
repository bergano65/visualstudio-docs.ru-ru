---
title: Установка версии публикации ClickOnce | Документация Майкрософт
description: Узнайте, как задать свойство версии публикации ClickOnce, которое определяет, является ли приложение обновлением.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885031"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Практическое руководство. Установка версии публикации приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Свойство определяет, будет ли публикуемое приложение рассматриваться как обновление. Каждый раз, когда версия увеличивается, приложение будет опубликовано как обновление.

 Это `Publish Version` свойство можно задать на странице **Публикация** **конструктора проектов**.

> [!NOTE]
> Существует параметр проекта, который будет автоматически увеличивать свойство при `Publish Version` каждом публикации приложения. Этот параметр включен по умолчанию. Дополнительные сведения см. в разделе [инструкции. автоматическое увеличение версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Изменение версии публикации

1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В поле **Версия публикации** Увеличьте номер версии **основного**, **дополнительного**, Номера **сборки** или **редакции** .

    > [!NOTE]
    > Не следует уменьшать номер версии. Это может привести к непредсказуемому поведению обновления.

## <a name="see-also"></a>См. также раздел
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Как автоматически увеличивать версию публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)