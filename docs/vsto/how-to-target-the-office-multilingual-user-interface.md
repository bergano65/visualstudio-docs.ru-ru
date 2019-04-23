---
title: Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c495f8a83b58c53404056befd2227b295c3324d5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063989"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office
  Многоязыкового интерфейса пользователя (MUI) является компонентом Microsoft Office, который позволяет пользователю изменить язык пользовательского интерфейса (UI). Например пользователь, работающий с английский интерфейс пользователя можно изменить язык интерфейса на испанский язык.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Если приложение будет использоваться с использованием многих языков Office, можно добавить код, чтобы автоматически изменить язык строк пользовательского интерфейса в соответствии с языком, который используется Microsoft Office на компьютере пользователя (если пользователь имеет установлены соответствующие ресурсы).

## <a name="to-check-the-current-office-ui-setting"></a>Чтобы проверить текущее состояние пользовательского интерфейса Office

1. Используйте <xref:System.Threading.Thread.CurrentUICulture%2A> свойство текущего потока. Задайте язык строк пользовательского интерфейса в соответствии с используемой версии Office, которая в настоящее время работает на компьютере пользователя.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)
