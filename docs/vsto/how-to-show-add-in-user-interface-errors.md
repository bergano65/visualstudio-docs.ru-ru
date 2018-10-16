---
title: 'Практическое: надстройка Показать ошибки пользовательского интерфейса'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd6da0c83d0dee835169a0a8068af8d75facbbd4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674763"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Практическое: надстройка Показать ошибки пользовательского интерфейса
  По умолчанию если надстройка VSTO при попытке управления пользовательским интерфейсом (UI) Microsoft Office и происходит сбой, сообщение об ошибке не отображается. Однако можно настроить приложения Microsoft Office для отображения сообщений об ошибках, связанных с пользовательским интерфейсом. Эти сообщения можно использовать для определения, почему настраиваемая лента не отображается, или почему лента появилась, но не отображаются элементы управления.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>Вывод ошибок пользовательского интерфейса надстройки VSTO  
  
1.  Запустите приложение.  
  
2.  Перейдите на вкладку **Файл** .  
  
3.  Щелкните **Параметры**.  
  
4.  В области категорий щелкните **Дополнительно**.  
  
5.  В области сведений выберите **Показать ошибки пользовательского интерфейса надстройки VSTO**, а затем нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  В Outlook флажок **Показать ошибки пользовательского интерфейса надстройки VSTO** находится в разделе **разработчика** в области сведений. Для других приложений этот флажок находится в разделе **Общие** в области сведений.  
  
## <a name="see-also"></a>См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)  
  
  