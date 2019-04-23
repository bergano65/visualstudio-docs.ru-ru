---
title: Практическое руководство. Программное создание документов Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61fb1302ffb0a068122c333e196178dfa2b30d86
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078945"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Практическое руководство. Программное создание документов Visio
  При создании нового документа Microsoft Office Visio вы добавляете его в коллекцию `Microsoft.Office.Interop.Visio.Documents` открытых документов Visio. Соответственно, метод `Microsoft.Office.Interop.Visio.Documents.Add` создает новый документ Visio. Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Создание новых пустых документов

### <a name="to-create-a-new-document"></a>Создание нового документа

- Используйте метод `Microsoft.Office.Interop.Visio.Documents.Add` для создания нового пустого документа не на основе шаблона.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Создание документов, скопированных из существующих документов
 Метод `Microsoft.Office.Interop.Visio.Documents.Add` может создать новый документ, который является копией существующего документа Visio. Вы должны указать имя файла и полный путь к диаграмме.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Создание нового документа, скопированного из существующего документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к диаграмме Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Создание наборов элементов, скопированных из существующих наборов элементов
 Метод [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) может создать новый набор элементов, который является копией существующего набора элементов Visio. Вы должны указать имя файла и полный путь к набору элементов.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Создание нового набора элементов, скопированного из существующего набора элементов

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к набору элементов.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Создание документов на основе существующих шаблонов
 `Microsoft.Office.Interop.Visio.Documents.Add` Метод может создать новый документ ( *.vsd* файл), основанный на существующем шаблоне Visio ( *.vst* файла). Этот метод копирует наборы элементов, стили и параметры, которые являются частью рабочей области шаблона. Необходимо указать имя файла и полный путь к шаблону.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Создание нового документа на основе существующего шаблона

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к шаблону.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).

- Документ Visio с именем `myStencil.vss` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).

- Документ Visio с именем `myTemplate.vst` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).

## <a name="see-also"></a>См. также
- [Решения Visio](../vsto/visio-solutions.md)
- [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Практическое руководство. Открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
