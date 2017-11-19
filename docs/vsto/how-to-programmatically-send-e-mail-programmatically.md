---
title: "Как: отправка электронной почты | Документы Microsoft"
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
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b0eefafa86fdaf8f7a664ac75a2f7c71a43549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-send-e-mail"></a>Как: отправка по электронной почте  
  Этот пример отправляет сообщение электронной почты, контакты, имеющие имя домена **example.com** в адресах электронной почты.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, имя домена **example.com** в адресах электронной почты.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Не удаляйте код фильтра, который ищет имя домена **example.com**. Решение будет отправлять сообщения электронной почты для всех контактов, при удалении фильтра.  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами почты](../vsto/working-with-mail-items.md)   
 [Как: программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Как: программный доступ к контактам](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  