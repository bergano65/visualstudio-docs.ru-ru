---
title: 'Как: программный поиск адреса электронной почты в контактах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 16b79f5f14f1e0d8c5c82a00f5f2ccf2412b991b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Практическое руководство. Программный поиск адреса электронной почты в контактах
  В этом примере в папке контактов осуществляется поиск контактов, в адресах электронной почты которых содержится доменное имя **example.com** .  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, в адресах электронной почты которых содержится доменное имя **example.com** (например, `somebody@example.com`), а также имеющие имена и фамилии.  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами контактов](../vsto/working-with-contact-items.md)   
 [Как: отправка по электронной почте](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Как: программный доступ к контактам](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  