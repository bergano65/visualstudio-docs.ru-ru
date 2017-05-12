---
title: "Практическое руководство. Автоматическое заполнение диапазонов данными, значения которых изменяются с постоянным шагом, с помощью программных средств | Microsoft Docs"
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
  - "Autofill - метод [Excel]"
  - "автоматическое заполнение диапазонов"
  - "диапазоны, автоматическое заполнение"
  - "книги, заполнение диапазонов"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Практическое руководство. Автоматическое заполнение диапазонов данными, значения которых изменяются с постоянным шагом, с помощью программных средств
  Метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> объекта <xref:Microsoft.Office.Interop.Excel.Range> используется для автоматического заполнения диапазона на листе значениями.  Чаще всего метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> используется для сохранения в диапазоне значений, увеличивающихся или уменьшающихся с определенным шагом.  Чтобы задать необходимое поведение, укажите необязательную константу из перечисления <xref:Microsoft.Office.Interop.Excel.XlAutoFillType>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 При использовании метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> необходимо указать два диапазона:  
  
-   диапазон, вызывающий метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>, в котором указывается начальная точка заполнения и содержится начальное значение;  
  
-   диапазон, который требуется заполнить, переданный в качестве параметра методу <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  Целевой диапазон должен включать диапазон с начальным значением.  
  
    > [!NOTE]  
    >  Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> нельзя передавать вместо элемента управления <xref:Microsoft.Office.Interop.Excel.Range>.  Дополнительные сведения см. в разделе [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## Компиляция кода  
 Первая ячейка диапазона заполняемого диапазона должна содержать начальное значение.  
  
 В данном примере необходимо заполнить три указанных ниже диапазона.  
  
-   Столбец B предназначен для хранения пяти дней недели.  В качестве начального значения введите в ячейку B1 слово **Понедельник**.  
  
-   Столбец C предназначен для хранения пяти месяцев.  В качестве начального значения введите в ячейку C1 слово **Январь**.  
  
-   Столбец D предназначен для хранения ряда чисел, каждое из которых на 2 больше предыдущего.  В качестве начальных значений введите в ячейку D1 значение **4**, а в ячейку D2 — значение **6**.  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  