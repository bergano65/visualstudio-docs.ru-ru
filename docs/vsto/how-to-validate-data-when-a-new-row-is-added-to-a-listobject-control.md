---
title: "Практическое руководство. Обработка данных при добавлении новой строки в элемент управления ListObject | Microsoft Docs"
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
  - "элементы управления [разработка решений Office в Visual Studio], проверка данных"
  - "элемент управления ListObject, новая строка"
  - "элемент управления ListObject, проверка данных"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Практическое руководство. Обработка данных при добавлении новой строки в элемент управления ListObject
  Пользователи могут добавлять новые строки в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Вы можете проверять данные пользователя перед фиксацией изменений в источнике данных.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Проверка данных  
 Каждый раз, когда строка добавляется в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, возникает событие <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>. Это событие можно обработать для выполнения проверки данных. Например, если приложение требует, чтобы в источник данных добавлялись только сотрудники в возрасте от 18 до 65 лет, можно проверять, что возраст попадает в этот диапазон, перед добавлением строки.  
  
> [!NOTE]  
>  Всегда следует проверять входные данные пользователя на сервере, как и на клиенте. Дополнительные сведения см. в разделе [Защищенные клиентские приложения](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01).  
  
#### Проверка данных при добавлении новой строки в элемент управления ListObject с привязкой к данным  
  
1.  Создайте переменные для идентификатора и объекта <xref:System.Data.DataTable> на уровне класса.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  Создайте новый объект <xref:System.Data.DataTable> и добавьте примеры столбцов и данных в обработчик событий `Startup` класса `Sheet1` \(в проекте уровня документа\) или класса `ThisAddIn` \(в проекте надстройки VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  Добавьте код в обработчик событий `list1_BeforeAddDataBoundRow`, чтобы проверить, попадает ли возраст в допустимый диапазон.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## Компиляция кода  
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1`.  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Сопоставление столбцов элемента управления ListObject данным](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  