---
title: Позднее связывание в решениях Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c886305b3cfe63ef2d2821752d97099d93689891
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847260"
---
# <a name="late-binding-in-office-solutions"></a>Позднее связывание в решениях Office
  Некоторые типы в объектных моделях приложений Office предоставляют функциональные возможности, доступные через компоненты позднего связывания. Например некоторые методы и свойства могут возвращать различные типы объектов в зависимости от контекста приложения Office, и некоторые типы могут предоставлять различные методы или свойства в различных контекстах.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Проекты Visual Basic, где **Option Strict** Выкл и Visual C# проектах, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] может работать непосредственно с типами, которые реализуют эти компоненты позднего связывания.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Явное и неявное приведение объекта возвращаемые значения  
 Множество методов и свойств в Microsoft Office, основные сборки взаимодействия (PIA) возвращают <xref:System.Object> значения, поскольку они могут возвращать несколько различных типов объектов. Например <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> возвращает <xref:System.Object> так, как его возвращаемое значение может быть <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart> объекта, в зависимости от того, что такое активный лист.  
  
 При возвращении метода или свойства <xref:System.Object>, необходимо явным образом преобразовать (в Visual Basic) объект к правильному типу в проектах Visual Basic где **Option Strict** включен. Необходимо явно привести тип <xref:System.Object> возвращаемые значения в проектах Visual Basic где **Option Strict** отключен.  
  
 В большинстве случаев в справочной документации перечислены возможные типы возвращаемого значения для члена, который возвращает <xref:System.Object>. Преобразование или приведение объекта позволяет использовать IntelliSense для объекта в редакторе кода.  
  
 Сведения о преобразовании в Visual Basic см. в разделе [явные и неявные преобразования &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) и [функция CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Примеры  
 В следующем примере кода показано, как приведение объекта к определенному типу в проекте Visual Basic где **Option Strict** включен. В такой тип проекта, необходимо явно привести <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойства <xref:Microsoft.Office.Interop.Excel.Range>. В этом примере требуется проект Excel уровня документа с классом листа `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 В следующем примере кода демонстрируется неявное приведение объекта к определенному типу в проекте Visual Basic где **Option Strict** выключен или находится в визуальном элементе C# проектом, нацеленным [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этих типов проектов <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойство неявно приведен к <xref:Microsoft.Office.Interop.Excel.Range>. В этом примере требуется проект Excel уровня документа с классом листа `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Доступ к членам, которые доступны только через позднее связывание  
 Некоторые свойства и методы в основных сборках взаимодействия Office доступны только через позднее связывание. В проектах Visual Basic where **Option Strict** выключен или находится в визуальном элементе C# проектах, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], компоненты позднего связывания в этих языках можно использовать для доступа к членам с поздним связыванием. В проектах Visual Basic where **Option Strict** имеет значение on, следует использовать отражение для доступа к этим членам.  
  
### <a name="examples"></a>Примеры  
 В следующем примере кода показано, как получить доступ к членам с поздним связыванием в проекте Visual Basic где **Option Strict** выключен или находится в визуальном элементе C# проектом, нацеленным [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этом примере обращается к с поздним связыванием **имя** свойство **Открытие файла** диалоговое окно в Word. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класс в проекте Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 В следующем примере кода показано, как использовать отражение для выполнения той же задачи в проекте Visual Basic где **Option Strict** включен.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>См. также  
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Использование типа dynamic &#40;C&#35; руководство по программированию&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))  
 [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
