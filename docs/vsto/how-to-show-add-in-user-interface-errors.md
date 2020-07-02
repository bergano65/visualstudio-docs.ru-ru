---
title: Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49985589c021192454bf0dd58929c9ef5646aec9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545786"
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

## <a name="see-also"></a>См. также
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Обзор панели действий](../vsto/actions-pane-overview.md)
