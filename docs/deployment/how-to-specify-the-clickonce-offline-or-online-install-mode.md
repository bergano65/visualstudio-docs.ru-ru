---
title: Практическое руководство. Укажите ClickOnce в автономный режим или режим Интернет-установки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a050724733ad87d0c583639fe3b0acfd2d6299f7
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890573"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Практическое руководство. задание режима установки ClickOnce: автономного или через Интернет
`Install Mode` Для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения определяет, будут ли приложения доступны в автономном или интерактивном режиме. При выборе **приложение доступно только из сети**, пользователь должен иметь доступ к [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] расположение публикации (веб-страницы или общей папки) для запуска приложения. При выборе **приложение будет доступно в автономном режиме**, оно добавляет элементы к **запустить** меню и **Установка и удаление программ** диалоговое окно; пользователь — может запустить приложение, когда они не подключены.

`Install Mode` Может устанавливаться на **публикации** странице **конструктор проектов**.

> [!NOTE]
> `Install Mode` Также можно задать с помощью мастера публикации. Дополнительные сведения см. в разделе [Практическое руководство. опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Чтобы сделать приложение ClickOnce доступным через Интернет только

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В **режим установки и параметры** область, нажмите кнопку **приложение доступно только из сети** переключатель.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Чтобы сделать приложение ClickOnce доступным сети или автономно

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В **режим установки и параметры** область, нажмите кнопку **приложение будет доступно в автономном режиме** переключатель.

     При установке приложения добавляет записи для **запустить** меню и **Установка и удаление программ** панели управления.

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)