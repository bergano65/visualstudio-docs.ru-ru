---
title: "Практическое руководство. Программная защита листов Excel | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "защита документов, добавление к листам"
  - "документы [разработка решений Office в Visual Studio], защита документов"
  - "защита, добавление к листам"
  - "листы, защита"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Программная защита листов Excel
  Функция защиты в Microsoft Office Excel помогает предотвратить изменение объектов на листе пользователями и кодом.  По умолчанию все ячейки заблокированы после включения защиты.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В настройках на уровне документа можно защитить листы с помощью конструктора Excel.  Лист также можно защитить программными средствами во время выполнения в проекте любого типа.  
  
> [!NOTE]  
>  Невозможно добавлять элементы управления Windows Forms в защищенные области листа.  
  
## Использование конструктора  
  
#### Защита листа в конструкторе  
  
1.  В группе **Изменения** вкладки **Рецензирование** щелкните **Защитить лист**.  
  
     Откроется диалоговое окно **Защита листа**.  Вы можете задать пароль и при необходимости указать определенные действия, которые пользователям разрешено выполнять с листом, например форматирование ячеек или вставка строк.  
  
 Также можно разрешить пользователям редактировать определенные диапазоны защищенных рабочих листов.  
  
#### Включение редактирования в определенных диапазонах  
  
1.  В группе **Изменения** вкладки **Рецензирование** щелкните **Разрешить изменение диапазонов**.  
  
     Откроется диалоговое окно **Разрешить изменение диапазонов**.  Можно указать диапазоны, которые разблокируются с помощью пароля, и пользователей, которым разрешено редактировать диапазоны без пароля.  
  
## Использование кода во время выполнения  
 Следующий код задает пароль \(с помощью переменной getPasswordFromUser, которая содержит пароль, полученный от пользователя\) и разрешает только сортировку.  
  
#### Защита листа с помощью кода в настройке на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> листа.  В этом примере предполагается, что вы работаете с листом `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### Защита листа с помощью кода в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> активного листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное снятие защиты с листов](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Практическое руководство. Программная защита книг Excel](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  