---
title: "Как: целевой многоязыкового пользовательского интерфейса Office | Документы Microsoft"
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
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39ee8b6bdcb4ad647164ec555cfa37ee9cfe8f50
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office
  Многоязычного пользовательского интерфейса (MUI) — это компонент Microsoft Office, который дает пользователю возможность изменить язык пользовательского интерфейса (UI). Например пользователь, работающий в английском пользовательском интерфейсе можно изменить язык интерфейса на испанский язык.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если ваше приложение будет использоваться с использованием нескольких языков Office, можно добавить код, чтобы автоматически изменять язык строк пользовательского интерфейса в соответствии с языком, который используется Office на компьютере пользователя (если у пользователя есть установлены соответствующие ресурсы).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Чтобы проверить текущие настройки пользовательского интерфейса Office  
  
1.  Используйте <xref:System.Threading.Thread.CurrentUICulture%2A> свойство текущего потока. Задайте язык строк пользовательского интерфейса в соответствии с языком, который используется в этой версии Office, запущенных на компьютере пользователя.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>См. также  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)  
  
  