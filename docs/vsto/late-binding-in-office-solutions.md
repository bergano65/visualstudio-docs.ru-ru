---
title: "Позднее связывание в решениях Office"
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
  - "объекты [разработка решений Office в Visual Studio], приведение"
  - "типы [разработка решений Office в Visual Studio], приведение"
  - "автоматизация [разработка решений Office в Visual Studio], приведение объектов"
  - "приведение объекта к указанному типу"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Позднее связывание в решениях Office
  Некоторые типы в объектных моделях приложений Office предоставляют функции, доступные через компоненты позднего связывания.  Например, некоторые методы и свойства могут возвращать различные типы объектов в зависимости от контекста приложения Office, а некоторые типы могут предоставлять различные методы или свойства в различных контекстах.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Проекты Visual Basic в **Option Strict** и проекты Visual C\#, целевой объект [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] может работать непосредственно с типами, которые используют эти функции позднего связывания.  
  
## Неявное и явное приведение возвращаемых значений объекта  
 Многие методы и свойства основной сборки взаимодействий в Microsoft Office \(PIA\) возвращают значения <xref:System.Object>, так как они возвращают различные типы объектов.  Например, свойство <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> возвращает объект <xref:System.Object>, так как его возвращаемое значение может быть объектом <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart> в зависимости от активного листа.  
  
 Когда метод или свойство возвращают <xref:System.Object>, необходимо явным образом преобразовать \(в Visual Basic\) объект к нужному вводится в проектах Visual Basic, где параметр **Option Strict** включен.  Нет необходимости явно привести возвращаемые значения <xref:System.Object> в проектах Visual Basic, **Option Strict**.  
  
 В большинстве случаев в справочной документации приведен список возможных типов возвращаемых значений для элемента, который возвращает объект <xref:System.Object>.  Преобразование или приведение в правильный формат объектов активирует IntelliSense для работы с объектами в Code Editor.  
  
 Общие сведения о преобразовании в Visual Basic см. в разделах [Явные и неявные преобразования &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) и [Функция CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Примеры  
 В следующем примере кода показано, как привести объект к определенному типу в проект Visual Basic, где параметр **Option Strict** включен.  В этом типе проекта необходимо явно привести свойство <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> к <xref:Microsoft.Office.Interop.Excel.Range>.  Для данного примера требуется проект Excel на уровне документа с классом листа `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 В следующем примере кода показывается неявное приведение объекта к определенному типу в проекте Visual Basic с отключенным параметром **Option Strict** или в проекте Visual C\#, предназначенном для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  В этих типах проектов необходимо свойство <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> неявным образом приводится к <xref:Microsoft.Office.Interop.Excel.Range>.  Для данного примера требуется проект Excel на уровне документа с классом листа `Sheet1`.  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## Доступ к элементам, доступным только через позднее связывание  
 Некоторые свойства и методы в основных сборках взаимодействия Office доступны только с помощью позднего связывания.  В проектах Visual Basic, **Option Strict** из или в проектах Visual C\# \- \#, целевой объект [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], можно использовать функции позднего связывания в этих языках из\-за привязанные к членам.  В проектах Visual Basic, где параметр **Option Strict** включен, необходимо использовать отражение для доступа к этим членам.  
  
### Примеры  
 В следующем примере кода показывается обращение к элементам с поздним связыванием в проекте Visual Basic с отключенным параметром **Option Strict** или в проекте Visual C\#, предназначенном для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  В этом примере выполняется обращение к свойству **Name** диалогового окна Word **Открытие файла** с поздним связыванием.  Чтобы использовать следующий пример кода, запустите его в проекте Word из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 В следующем примере кода показано, как использовать отражение для выполнения той же задачи в проекте Visual Basic, где параметр **Option Strict** включен.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## См. также  
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Использование типа dynamic &#40;Руководство по программированию на C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Отражение &#40;C&#35; и Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  