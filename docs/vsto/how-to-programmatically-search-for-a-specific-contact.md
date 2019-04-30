---
title: Практическое руководство. Программный поиск определенного контакта
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: feff583d28bf53f4bffc9b425d52902688b80a4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000320"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Практическое руководство. Программный поиск определенного контакта
  В этом примере выполняется поиск определенного контакта в папке контактов Outlook по имени и фамилии. В этом примере предполагается, что в папке контактов есть контакт с именем **John Evans** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>См. также
- [Работа с элементами контактов](../vsto/working-with-contact-items.md)
- [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
