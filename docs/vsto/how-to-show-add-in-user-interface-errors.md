---
title: "Как: Показывать ошибки интерфейса пользователя надстроек | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b483889dbd970b2225c773e6dd43b9333b0d8a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Практическое руководство. Просмотр ошибок пользовательского интерфейса надстройки
  По умолчанию, если происходит сбой надстройки VSTO при попытке управления пользовательским интерфейсом Microsoft Office, сообщение об ошибке не отображается. Однако можно настроить приложения Microsoft Office для отображения сообщений об ошибках, связанных с пользовательским интерфейсом. Эти сообщения можно использовать для определения, почему настраиваемая лента не появляется или почему лента появилась, но не отображаются элементы управления.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Вывод ошибок пользовательского интерфейса надстройки VSTO  
  
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
  
  