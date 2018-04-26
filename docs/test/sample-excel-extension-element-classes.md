---
title: Пример расширения Excel. Классы Element
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a254f85a27c650bf8d8b64d2460ebad88e3befc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-element-classes"></a>Пример расширения Excel. Классы Element
Расширение использует классы, которые являются производными от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> и представляют элементы управления "Лист" и "Ячейка" в приложении [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 Базовым элементом для данного расширения является `ExcelElement`. От этого элемента наследуются классы `ExcelWorksheetElement` и `ExcelCellElement`.

## <a name="element-and-elementinformation-classes"></a>Классы Element и ElementInformation
 `Element` является базовым классом для всех элементов пользовательского интерфейса для расширения Excel; он является производным от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>. `ElementInformation` является базовым классом для классов информации об элементах в примере; он не содержит членов.

#### <a name="simple-properties-and-methods"></a>Простые свойства и методы
 Эти члены возвращают простые значения, например значение свойства `Name` или `ClassName`; код этих членов является простым и удобным для восприятия. Некоторые значения возвращаются с помощью класса `Utility`, который рассматривается ниже. Прочие члены возвращают значение `null`, так как они не имеют отношения к этому примеру расширения. Два члена имеют большее значение по сравнению с остальными: свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> и метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.

#### <a name="queryid-property"></a>Свойство QueryId
 Это свойство возвращает условие, составленное из пар "имя — значение свойства", которое уникальным образом определяет элемент управления во время воспроизведения. Разработчику необходимо переопределить это свойство в каждом производном классе элемента управления, чтобы возвращался объект <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, который может использоваться платформой для поиска элемента управления в пользовательском интерфейсе.

#### <a name="cacheproperties-method"></a>Метод CacheProperties
 Этот метод вызывается платформой тестирования во время процесса записи и предписывает элементу сохранить снимок важных свойств. Благодаря этому свойства остаются доступными, даже если фактический элемент управления пользовательского интерфейса больше не отображается на экране.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>Классы WorksheetElement и WorksheetInformation
 Класс `WorksheetElement` представляет лист Excel в платформе тестирования; он наследуется от базового класса `Element`. Для предоставления конкретной информации об объекте листа Excel переопределяются три свойства: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> и <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.

 К этому классу также применяется атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute>, чтобы сделать класс видимым для модели COM.

 Класс `WorksheetInformation` представляет информацию о листе Excel. У него имеется только один член — свойство `SheetName`, однако этого достаточно для данного примера.

## <a name="cellelement-and-cellinformation-classes"></a>Классы CellElement и CellInformation
 Класс `CellElement` представляет ячейку Excel; он наследуется от базового класса `Element`. Его единственным переопределенным членом является свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, которое возвращает объект <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, использующий свойства `RowIndex` и `ColumnIndex` для определения ячейки.

## <a name="utilities-and-excelutilities-classes"></a>Классы Utilities и ExcelUtilities
 Внутренний класс `ExcelUtilities` предоставляет некоторые константные значения, такие как имя технологии, а также метод, который определяет, действительно ли указанный дескриптор окна представляет лист Excel.

 Класс `Utilities` содержит вспомогательные методы, которые возвращают различные сведения о пользовательском интерфейсе. Некоторые методы используют прямые вызовы внешних системных библиотек DLL, таких как **USER32.DLL** и **OLEACC.DLL**, для получения дескрипторов окон из пользовательского интерфейса **.**

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
