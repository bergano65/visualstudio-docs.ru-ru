---
title: 'Практическое: программное создание документов Visio'
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
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256748"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Практическое: программное создание документов Visio
  Когда вы создаете новый документа документа Microsoft Office Visio, можно добавить его `Microsoft.Office.Interop.Visio.Documents` коллекцию открытых документов Visio. Следовательно `Microsoft.Office.Interop.Visio.Documents.Add` метод создает новый документ Visio. Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="create-new-blank-documents"></a>Создание новых пустых документов  
  
### <a name="to-create-a-new-document"></a>Создание нового документа  
  
-   Используйте `Microsoft.Office.Interop.Visio.Documents.Add` метод для создания нового пустого документа не зависит от шаблона.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Создание документов, скопированных из существующих документов  
 `Microsoft.Office.Interop.Visio.Documents.Add` Метод может создать новый документ, который является копией существующего документа Visio. Вы должны указать имя файла и полный путь к диаграмме.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Создание нового документа, скопированного из существующего документа  
  
-   Вызовите `Microsoft.Office.Interop.Visio.Documents.Add` метод и указать путь к диаграмме Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Создание наборов элементов, скопированных из существующих наборов элементов  
 Метод [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) может создать новый набор элементов, который является копией существующего набора элементов Visio. Вы должны указать имя файла и полный путь к набору элементов.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Создание нового набора элементов, скопированного из существующего набора элементов  
  
-   Вызовите `Microsoft.Office.Interop.Visio.Documents.Add` метод и укажите путь к набору элементов.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Создание документов на основе существующих шаблонов  
 `Microsoft.Office.Interop.Visio.Documents.Add` Метод может создать новый документ ( *.vsd* файл), основанный на существующем шаблоне Visio ( *.vst* файла). Этот метод копирует наборы элементов, стили и параметры, которые являются частью рабочей области шаблона. Необходимо указать имя файла и полный путь к шаблону.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Создание нового документа на основе существующего шаблона  
  
-   Вызовите `Microsoft.Office.Interop.Visio.Documents.Add` метод и указать путь к шаблону.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).  
  
-   Документ Visio с именем `myStencil.vss` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).  
  
-   Документ Visio с именем `myTemplate.vst` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Как: открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Практическое: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое: программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое: программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  