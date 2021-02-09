---
title: Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки
description: Узнайте, как можно использовать Visual Studio для программного отображения ошибок пользовательского интерфейса надстройки ВТСО в приложениях Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e07e49d901b44b534d9d274e5535be663e97ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927682"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки
  По умолчанию, если надстройка VSTO пытается управлять пользовательским интерфейсом Microsoft Office и завершается ошибкой, сообщение об ошибке не отображается. Однако можно настроить приложения Microsoft Office для отображения сообщений об ошибках, связанных с пользовательским интерфейсом. Эти сообщения можно использовать для определения причины, по которой пользовательская лента не отображается, или для отображения ленты, но не для отображения элементов управления.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Вывод ошибок пользовательского интерфейса надстройки VSTO

1. Запустите приложение.

2. Перейдите на вкладку **Файл** .

3. Щелкните **Параметры**.

4. В области категорий щелкните **Дополнительно**.

5. В области сведений выберите **Показать ошибки пользовательского интерфейса надстройки VSTO**, а затем нажмите кнопку **ОК**.

    > [!NOTE]
    > В Outlook флажок **Показать ошибки пользовательского интерфейса надстройки VSTO** находится в разделе **разработчика** в области сведений. Для других приложений этот флажок находится в разделе **Общие** в области сведений.

## <a name="see-also"></a>См. также раздел
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Обзор панели действий](../vsto/actions-pane-overview.md)
