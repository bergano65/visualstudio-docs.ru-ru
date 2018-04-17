---
title: 'Как: отправка электронной почты | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3ee656a8a4965f01969bad19d66d0ea6215bcbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
  