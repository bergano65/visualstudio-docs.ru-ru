---
title: 'Как: программное создание документов Visio | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2dd64b2996df4ed75cd45cd741619658f9b3654
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Практическое руководство. Программное создание документов Visio
  При создании нового документа Microsoft Office Visio, можно добавить в Microsoft.Office.Interop.Visio.Documents коллекцию открытых документов Visio. Следовательно метод Microsoft.Office.Interop.Visio.Documents.Add создает новый документ Visio. Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="creating-new-blank-documents"></a>Создание новых пустых документов  
  
#### <a name="to-create-a-new-document"></a>Создание нового документа  
  
-   Используйте метод Microsoft.Office.Interop.Visio.Documents.Add для создания нового пустого документа не основан на шаблоне.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Создание документов, скопированных из существующих документов  
 Метод Microsoft.Office.Interop.Visio.Documents.Add можно создать новый документ, который является копией существующего документа Visio. Вы должны указать имя файла и полный путь к диаграмме.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Создание нового документа, скопированного из существующего документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к диаграмме Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Создание наборов элементов, скопированных из существующих наборов элементов  
 Метод [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) может создать новый набор элементов, который является копией существующего набора элементов Visio. Вы должны указать имя файла и полный путь к набору элементов.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Создание нового набора элементов, скопированного из существующего набора элементов  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к набору элементов.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Создание документов на основе существующих шаблонов  
 Метод Microsoft.Office.Interop.Visio.Documents.Add можно создать новый документ (VSD-файл), основанный на существующем шаблоне Visio (VST-файле). Этот метод копирует наборы элементов, стили и параметры, которые являются частью рабочей области шаблона. Необходимо указать имя файла и полный путь к шаблону.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Создание нового документа на основе существующего шаблона  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к шаблону.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" (для Windows XP и более ранних версий) или в папке "Документы" (для Windows Vista).  
  
-   Документ Visio с именем `myStencil.vss` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" (для Windows XP и более ранних версий) или в папке "Документы" (для Windows Vista).  
  
-   Документ Visio с именем `myTemplate.vst` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" (для Windows XP и более ранних версий) или в папке "Документы" (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Как: открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Как: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Как: программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  