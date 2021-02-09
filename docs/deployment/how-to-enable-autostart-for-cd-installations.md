---
title: Включить автозапуск для установок компакт-дисков | Документация Майкрософт
description: Узнайте, как включить автозапуск при развертывании приложения ClickOnce с помощью съемных носителей, таких как компакт-диски или DVD-диски.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b157df8666223e72a1e36d58505a5c087b0351bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900679"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Практическое руководство. Включение автозапуска при установке с компакт-диска
При развертывании [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью съемных носителей, таких как компакт-диски или DVD-диски, можно включить, `AutoStart` чтобы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение автоматически запускалось при вставке носителя.

 `AutoStart` можно включить на странице **Публикация** **конструктора проектов**.

### <a name="to-enable-autostart"></a>Включение автозапуска

1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. Нажмите кнопку **Параметры** .

     Откроется диалоговое окно " **Параметры публикации** ".

4. Щелкните **Развертывание**.

5. Установите флажок **для установки с компакт-диска, автоматически запускать при вставке** .

     При публикации приложения файл *Autorun. INF* будет скопирован в место публикации.

## <a name="see-also"></a>См. также раздел
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)