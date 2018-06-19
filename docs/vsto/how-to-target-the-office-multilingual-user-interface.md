---
title: 'Как: целевой многоязыкового пользовательского интерфейса Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262037"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Как: целевой многоязыкового пользовательского интерфейса Office
  Многоязычного пользовательского интерфейса (MUI) — это компонент Microsoft Office, который дает пользователю возможность изменить язык пользовательского интерфейса (UI). Например пользователь, работающий в английском пользовательском интерфейсе можно изменить язык интерфейса на испанский язык.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если ваше приложение будет использоваться с использованием многих языков Office, можно добавить код, чтобы автоматически изменять язык строк пользовательского интерфейса в соответствии с языком, который используется Office на компьютере пользователя (если у пользователя есть установлены соответствующие ресурсы).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Чтобы проверить текущие настройки пользовательского интерфейса Office  
  
1.  Используйте <xref:System.Threading.Thread.CurrentUICulture%2A> свойство текущего потока. Задайте язык строк пользовательского интерфейса в соответствии с языком, который используется в версии Office, которая в настоящее время выполняется на компьютере пользователя.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>См. также  
 [Как: Office целевых приложений с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)  
  
  